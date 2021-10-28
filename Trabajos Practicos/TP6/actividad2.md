## GENERAR IMAGEN DE DOCKER

* Compilamos la salida
(mvnCleanPackage.PNG)

* Generamos la imagen de docker con el comando `docker build -t test-spring-boot .`
(dockerBuildTest.PNG)

* Ejecutamos el contenedor con `docker run -p 8080:8080 test-spring-boot` 
(dockerRunTest.PNG)

* Hacemos un curl `curl -v localhost:8080` y verificamos que nos devuelve.
(curl.PNG)
