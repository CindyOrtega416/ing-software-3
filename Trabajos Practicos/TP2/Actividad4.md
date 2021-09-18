## Actividad 4

![image](https://user-images.githubusercontent.com/37404924/129836584-2f7cbe8e-e0dd-4921-9258-319fb94c7697.png)

Corremos el comando y no ocurre nada porque no indicamos el comando correspondiente para ser ejecutado

![image](https://user-images.githubusercontent.com/37404924/129836732-9b7862f0-40c6-46a6-9452-5a46306e0504.png)

En este caso si obtuvimos un resultado al ejecutar un comando dentro del contenedor

A continuación listamos los contenedores:
![tempsnip](https://user-images.githubusercontent.com/37404924/129837791-0d61f203-18cf-431a-9528-4cc76b85ede5.png)


Como podemos observar, el primer comando 'docker ps' lista solo los contenedores que estan corriendo, donde en nuestro caso, no tenemos ninguno.
El segundo comando 'docker ps -a' podemos ver **todos** los contenedores, dado que la flag -a es equivalente a *--all*
