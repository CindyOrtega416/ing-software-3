## DOCKERFILES MULTI ETAPAS

* Modificamos el Dockerfile

* Construimos nuevamente la imagen con `docker build -t test-spring-boot .`
(newBuild.PNG)
(newBuild1.PNG)

* ¿Cómo se estructura el dockerfile munti-stage que acabamos de crear?:
** Comenzamos especificando aquellos archivos que se deben copiar para descargar las dependencias necesarias para la ejecución del sistema:
```
FROM maven:3.5.2-jdk-8-alpine AS MAVEN_TOOL_CHAIN
COPY pom.xml /tmp/
RUN mvn -B dependency:go-offline -f /tmp/pom.xml -s /usr/share/maven/ref/settings-docker.xml
 
```

**Luego, lo que se hace es construir (build) el proyecto copiando previamente los archivos fuente:

```
COPY src /tmp/src/
WORKDIR /tmp/
RUN mvn -B -s /usr/share/maven/ref/settings-docker.xml package

```

** Por último, se ejecuta la aplicación:

```
FROM java:8-jre-alpine

EXPOSE 8080

RUN mkdir /app
COPY --from=MAVEN_TOOL_CHAIN /tmp/target/*.jar /app/spring-boot-application.jar

ENV JAVA_OPTS="-Xms32m -Xmx128m"

ENTRYPOINT exec java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app/spring-boot-application.jar

HEALTHCHECK --interval=1m --timeout=3s CMD wget -q -T 3 -s http://localhost:8080/actuator/health/ || exit 1

```