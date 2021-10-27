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
![image](https://user-images.githubusercontent.com/37404924/138983443-421aba56-ad8a-4993-86fb-8db691f36ee0.png)

 
Para el cual, luego de buscar en internet una solución, encontré que agregando la siguiente línea de código en el archivo POM, esto se resolvía:

![image](https://user-images.githubusercontent.com/37404924/138983469-97931c7a-b50d-4b4b-a8ec-c08d10a36dde.png)

 
Quedando:

![image](https://user-images.githubusercontent.com/37404924/138983485-cebc3b44-88ca-47cf-9d15-5cacdf6714c0.png)

 
Luego, ejecutamos:
`java -cp target/ejemplo-1.0-SNAPSHOT.jar ar.edu.ucc.App `

![image](https://user-images.githubusercontent.com/37404924/138983503-8787b40d-0753-4803-9927-7a13586ceee0.png)

 
Y hemos creado un proyecto java a partir del template ar.edu.ucc, el cual se ha ejecutado exitosamente 
