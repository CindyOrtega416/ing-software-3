Generamos un nuevo proyecto en el directorio:
`mvn archetype:generate -DgroupId=ar.edu.ucc -DartifactId=ejemplo -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false `
Y obtenemos esta estructura:
`.
└── ejemplo
    ├── pom.xml
    └── src
        ├── main
        │   └── java
        │       └── ar
        │           └── edu
        │               └── ucc
        │                   └── App.java
        └── test
            └── java
                └── ar
                    └── edu
                        └── ucc
                            └── AppTest.java

12 directories, 3 files ` 
Que consiste en un archive POM.xml, una carpeta src y una carpeta test.
Compilamos el proyecto con:
`mvn clean package `
Pero al ejecutar este comando se produjo el siguiente error:
 
Para el cual, luego de buscar en internet una solución, encontré que agregando la siguiente línea de código en el archivo POM, esto se resolvía:
 
Quedando:
 
Luego, ejecutamos:
`java -cp target/ejemplo-1.0-SNAPSHOT.jar ar.edu.ucc.App `
 
Y hemos creado un proyecto java a partir del template ar.edu.ucc, el cual se ha ejecutado exitosamente 
