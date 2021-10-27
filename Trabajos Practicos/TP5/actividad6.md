MANEJO DE DEPENDECIAS

•	Crear un nuevo proyecto con artifactId ejemplo-uber-jar
 
![image](https://user-images.githubusercontent.com/37404924/138983591-fa9ff5e2-837c-41b9-8453-dec88ef9da4f.png)


•	Modificar el código de App.java para agregar utilizar una librería de logging:
`package ar.edu.ucc;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

/**
 * Hello world!
 *
 */
public class App 
{
    public static void main( String[] args )
    {
        Logger log = LoggerFactory.getLogger(App.class);
        log.info("Hola Mundo!");
    }
} ´

Al compilar el código nos encontramos con el error de que las dependencia nos están cargadas en el POM.xml
 
 Las cargamos agregando en el POM.xml 
 
 ![image](https://user-images.githubusercontent.com/37404924/138983641-963dc9e5-68b1-44c3-9bef-d4286821209c.png)

`    <dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
      <version>1.2.1</version>
    </dependency> `

 ![image](https://user-images.githubusercontent.com/37404924/138983709-285c6256-5c8d-4722-adaf-1c0cd9cdc279.png)

+ 
El properties de la actividad anterior:
 
 ![image](https://user-images.githubusercontent.com/37404924/138983725-719c397a-dcfe-4025-8bfe-76ad15b9a1bf.png)

 
Una vez hecho esto, funciona perfectamente

![image](https://user-images.githubusercontent.com/37404924/138983732-b8c79ef8-0357-45a3-b8a1-d7eb5caa441a.png)

 
