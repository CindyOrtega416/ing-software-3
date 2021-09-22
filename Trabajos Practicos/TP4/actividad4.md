## DESARROLLO

### 1- Instanciación del sistema
A continuación se adjuntan imagenes del proceso de instalación y recorrido del sistema


### 2- Investigación de los componentes

* 1.Describa los contenedores creados, indicando cuales son los puntos de ingreso del sistema

Como hemos visto en clase, y utilizando como ejemplo a MercadoLibre, una arquitectura de microservicios (como lo es la aplicación web que hemos levantando sobre el localhost) consta de una colección de servicios autónomos y pequeños. Estos servicios son independientes entre sí.

Esta aplicación web se basa en una red con 15 containers, siendo el único punto de entrada al sistema el `edge-router`.

[Captura 1]

Habiamos visto que la puerta de enlace de API o 'API Gateway' es el punto de entrada para los clientes. Entonces, en lugar de llamar a los servicios directamente, los clientes llaman a la API Gateway, que reenvía la llamada a los servicios apropiados.

[microservices]

Nuestra API Gateway es el `edge-router` que se implementa gracias a Traefik, es cual es un servicio de load balancing que se encarga de redireccionar los request que llegan sobre el puerto `80` hacia el container de `front-end`, siendo este el API Gateway previamente mencionado.

[Captura] [traefik]

* 3. ¿Por qué cree usted que se está utilizando repositorios separados para el código y/o la configuración del sistema? Explique puntos a favor y en contra.

Se está utilizando repositorios separados por el concepto de microservicios. 
	* Los microservicios son pequeños e independientes, y están acoplados de forma imprecisa.
	*Cada servicio es un código base independiente
	*Los servicios pueden implementarse de manera independiente

Entonces, se están utilizando repos distintos ya que de esta forma se puede tener un seguimiento del proceso de evolución y de los cambios que se realicen a servicios individuales. Así como también generar pipelines separadas para cada servicio, lo que permite desplegarlos de forma independiente y así poder trabajar sobre ellos sin afectar a otros servicios.

Como punto en contra está la complejidad que este enfoque introduce en la administración de los repositorios

* 4.¿Cuál contenedor hace las veces de API Gateway?

El contenedor Front-end hace las veces de API Gateway

* 5.Cuando ejecuto `curl http://localhost/customers` 
 * 6.¿Cuál de todos los servicios está procesando la operación?
Primero, la request llega al `localhost` en donde se encuentra con el `edge-router`. Desde allí es redireccionada hacia el servicio `front-end`, el API Gateway.
Luego, esta termina siendo procesada por el servici `user`
[curl]

* 7 ¿Y para los siguientes casos?
`curl http://localhost/catalogue`
`curl http://localhost/tags` 

Estas requests siguen el mismo recorrido mencionado en el punto anterior, solo que difieren en que al llegar a la API Gateway, la request es reenviada y termina siendo procesada por el servicio `catalogue`

[curl1] [curl2]

* 8.¿Como perisisten los datos los servicios?
Cada servicio que requiere persistencia de datos (ej. user) tiene un container acompañante, en el cual persisten su datos (en el ejemplo dado, user-db_1). En este ejemplo se utiliza principalmente mongodb

[db]

* 9.¿Cuál es el componente encargado del procesamiento de la cola de mensajes?
`queue-master`

* 10.¿Qué tipo de interfaz utilizan estos microservicios para comunicarse?
Se comunican entre sí utilizando REST
