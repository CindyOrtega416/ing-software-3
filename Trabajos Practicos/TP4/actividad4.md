## DESARROLLO

### 1- Instanciación del sistema
A continuación se adjuntan imagenes del proceso de instalación y recorrido del sistema

![Captura2](https://user-images.githubusercontent.com/37404924/134284273-1265a2d4-0b55-484a-ad3e-bdd022933f9a.PNG)

![Captura3](https://user-images.githubusercontent.com/37404924/134284285-22f6a964-7fd1-45fa-89f5-001fc783dcf5.PNG)

![Captura4](https://user-images.githubusercontent.com/37404924/134284292-c6ccb8f2-82b2-443b-832b-645612c62763.PNG)

![Captura7](https://user-images.githubusercontent.com/37404924/134284330-bc6d8dec-8a8e-4437-b903-2341f7422eb6.PNG)

![Captura6](https://user-images.githubusercontent.com/37404924/134284345-7210b4eb-b2a7-41ba-9eb5-9f2fd3ee1f99.PNG)


### 2- Investigación de los componentes

* 1.Describa los contenedores creados, indicando cuales son los puntos de ingreso del sistema

Como hemos visto en clase, y utilizando como ejemplo a MercadoLibre, una arquitectura de microservicios (como lo es la aplicación web que hemos levantando sobre el localhost) consta de una colección de servicios autónomos y pequeños. Estos servicios son independientes entre sí.

Esta aplicación web se basa en una red con 15 containers, siendo el único punto de entrada al sistema el `edge-router`.

![Captura1](https://user-images.githubusercontent.com/37404924/134284402-09db6531-7ffc-4452-a9b2-c8df7b02dfe6.PNG)

Habiamos visto que la puerta de enlace de API o 'API Gateway' es el punto de entrada para los clientes. Entonces, en lugar de llamar a los servicios directamente, los clientes llaman a la API Gateway, que reenvía la llamada a los servicios apropiados.

![microservices](https://user-images.githubusercontent.com/37404924/134284425-b2f733a6-3ec6-422a-abc4-350056c434ac.PNG)

Nuestra API Gateway es el `edge-router` que se implementa gracias a Traefik, es cual es un servicio de load balancing que se encarga de redireccionar los request que llegan sobre el puerto `80` hacia el container de `front-end`, siendo este el API Gateway previamente mencionado.

![Captura](https://user-images.githubusercontent.com/37404924/134284439-5689361b-4dbf-4aed-8302-6ffc397eaa81.PNG) 

![traefik](https://user-images.githubusercontent.com/37404924/134284454-9947aa60-483b-448b-bd38-2f451393327b.PNG)


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

![curl](https://user-images.githubusercontent.com/37404924/134284475-58c5c7b1-5cd3-4dff-b22d-99935037dbab.PNG)

* 7 ¿Y para los siguientes casos?
`curl http://localhost/catalogue`
`curl http://localhost/tags` 

Estas requests siguen el mismo recorrido mencionado en el punto anterior, solo que difieren en que al llegar a la API Gateway, la request es reenviada y termina siendo procesada por el servicio `catalogue`

![curl1](https://user-images.githubusercontent.com/37404924/134284493-e8a848b5-36d4-462a-8662-a62fdb791f64.PNG)

![curl2](https://user-images.githubusercontent.com/37404924/134284504-dbd73a7e-8f7f-4e82-9c13-6bb7eafeff8c.PNG)


* 8.¿Como perisisten los datos los servicios?
Cada servicio que requiere persistencia de datos (ej. user) tiene un container acompañante, en el cual persisten su datos (en el ejemplo dado, user-db_1). En este ejemplo se utiliza principalmente mongodb

![db](https://user-images.githubusercontent.com/37404924/134284525-acad21e3-5551-4a7c-a7f7-47f394048753.PNG)

* 9.¿Cuál es el componente encargado del procesamiento de la cola de mensajes?
`queue-master`

* 10.¿Qué tipo de interfaz utilizan estos microservicios para comunicarse?
Se comunican entre sí utilizando REST
