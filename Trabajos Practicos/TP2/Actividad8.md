## Actividad 8

* Ejecutamos la imagen nyan/cat/web

![image](https://user-images.githubusercontent.com/37404924/129845110-91072714-ec13-4b76-a775-eaad6fab74fd.png)
 
 * Ejecutamos un docker ps y observamos que el contenedor esta corriendo en el puerto 80 y 443, pero si intentamos en un navegador acceder a http://localhost no sucede nada.

![image](https://user-images.githubusercontent.com/37404924/129845327-38649d4d-f5d5-4b00-a13b-46e5b9a9d8ca.png)

* Procedemos entonces a parar y remover este contenedor:

![image](https://user-images.githubusercontent.com/37404924/129845502-aa79e676-cffb-459f-bbd5-9560dc95e578.png)

* Vamos a volver a correrlo otra vez, pero publicando uno de los puertos solamente, en este caso el 80

![image](https://user-images.githubusercontent.com/37404924/129847752-e509fc6d-0561-412b-b8ee-52815e6562e8.png)

![image](https://user-images.githubusercontent.com/37404924/129847793-3d7ce866-b3ba-412a-b3b9-a64f97b9a666.png)
