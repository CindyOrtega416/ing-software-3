## Introducción a Maven

•	Qué es Maven?

Maven es una herramienta de software que se utiliza principalmente para facilitar la tarea de crear y administrar proyectos escritos en Java, C#, Ruby, Scala y otros lenguajes. 

Según su documentación oficial “El objetivo principal de Maven es permitir que un desarrollador comprenda el estado completo de su trabajo en un período de tiempo más corto.” Para lograr este objetivo, Maven se ocupa de varias áreas de interés:

o	Facilitando el proceso de construcción
o	Proporcionar un sistema de construcción uniforme
o	Proporcionar información de calidad sobre el proyecto
o	Fomentar mejores prácticas de desarrollo

•	Qué es el archivo POM?

POM son las siglas de Project Object Model. Es unidad fundamental de trabajo en Maven. Es un archivo XML que reside en el directorio base del proyecto como pom.xml.

El POM contiene información sobre el proyecto y varios detalles de configuración utilizados por Maven para construir los proyectos (build).

Debe haber un solo archivo POM para cada proyecto y sus elementos básicos son:
o	modelVersion: versión del proyecto descripto en el POM. Mientras se use Maven 3 debe estar seteado en 4.0.0.

o	groupId: Id del grupo de proyectos que lo identifica de entre todos los proyectos. Es único

o	artifactId: nombre del proyecto.

o	versionId: Versión del proyecto. Junto con groupId, se usa dentro del repositorio de un artefacto (proyecto) para llevar un registro de los cambios en el código o las versiones.

•	Repositorios:
En un repositorio de Maven se encuentran los proyectos, los cuales al estar estructurados de cierta forma permite hacer la descarga de las dependencias

o	Repositorio Local: es un directorio en la computadora que funciona como un caché para las descargas remotas y contiene artefactos de compilación temporales que son necesarios para la construcción del proyecto
o	Repositorio Central: es un repositorio donde se guardan todos los componentes utilizados por la comunidad que trabaja con JDK
o	Repositorio Remoto: hacen referencia a cualquier tipo de repositorio que puede ser accedido mediante protocolos como file:// y https:// para ser descargados e implementados

•	Entender Ciclos de vida de build:
Un ciclo de vida de construcción (build) es proporcionado por Maven con el objetivo de que el desarrollador logre realizar una gestión ágil y rápida de la configuración de su proyecto Maven.
En otras palabras, es un concepto (abstracto) que cubre todos los pasos que se espera que ocurran en la vida de desarrollo de un proyecto. Cuenta con tres ciclos de vida establecidos:
•	Default: Es el encargado del deployment del proyecto
•	Clean:  Es este ciclo se limpian los archivos y directorios generados por Maven durante el build.
•	Site: Es el ciclo encargado de la creación del proyecto y su documentación.
