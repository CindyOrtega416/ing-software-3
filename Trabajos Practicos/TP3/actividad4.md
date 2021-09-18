## ACTIVIDAD 4

![architecture](https://user-images.githubusercontent.com/37404924/133871692-0ff424d5-a280-472f-bdad-48d3df3a78f5.png)


El sistema utiliza dos networks:

front-tier, a través de la cuál se interconectan las apps de votación y resultados, utilizando websockets.
back-tier, a través de la cuál éstas se comunican con redis y postgres. A su vez, el worker de java se comunica con estas últimas, actualizando postgres a partir de redis.
La persistencia de datos de postgres se realiza sobre el volumen db-data.

Ambas aplicaciones web exponen su puerto 80 interno a través de los puertos 5000 y 5001 del host, respectivamente.

¿Que ocurre?
1. Ingreso del voto de un usuario por 'localhost:5000' a la aplicación python.
2. Ingreso de la información del voto desde la app de python a redis.
3. El worker de java esta observando la cola en redis, al momento en que ingresan votos los toma.
4. El worker ingresa a la db el voto tomado desde la cola.
5. La app node esta constantemente pidiendo los nuevos votos desde la db.
6.La app node visualiza la cuenta de votos en 'localhost:5001'.
