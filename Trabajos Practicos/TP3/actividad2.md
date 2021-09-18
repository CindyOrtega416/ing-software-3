ACTIVIDAD 2

Se trata de una API que esta conectada a la base de datos Redis y posee un contador que es incrementado al visitar el endpoint en ‘/’.

Los parámetros –e definen variables de entorno. En el punto anterior es utilizada para configurar el host y el puerto de Redis.

Si ejecuto docker rm -f web y vuelvo a correr 'docker run -d --net mybridge -e REDIS_HOST=db -e REDIS_PORT=6379 -p 5000:5000 --name web alexisfr/flask-app:latest' estaría eliminando el contenedor y al volver a levantarlo el contador no se reiniciaría, ya que solo hemos borrado la app web. 

Ahora, si ejecuto 'docker rm -f db' y lo levanto nuevamente lograré borrar los hits registrados.

Como posible solución, Docker permite crear volúmenes de datos para guardar información independientemente de los contenedores