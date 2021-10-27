MANEJO DE DEPENDECIAS

•	Crear un nuevo proyecto con artifactId ejemplo-uber-jar
 

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
} `

Al compilar el código nos encontramos con el error de que las dependencia nos están cargadas en el POM.xml
 
 Las cargamos agregando en el POM.xml 
`    <dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
      <version>1.2.1</version>
    </dependency> `

 
+ 
El properties de la actividad anterior:
 
Una vez hecho esto, funciona perfectamente
 

•	
