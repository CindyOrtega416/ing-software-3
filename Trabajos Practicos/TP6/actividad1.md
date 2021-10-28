## CONCEPTOS DE DOCKERFILES
* FROM: inicializa una nueva etapa de construcción y establece la imagen base para instrucciones posteriores.
* RUN: ejecuta cualquier comando sobre la imagen deseada.
* ADD: copia archivos, directorios o URL de archivos remotos y los agrega al sistema de archivos de la imagen.
* COPY: copia archivos o directorios y los agrega al sistema de archivos del contenedor. (NO ARCHIVOS REMOTOS)
* EXPOSE: informa a Docker que el contenedor escucha en los puertos especificados durante su ejecución.
* CMD: proporciona valores predeterminados para un contenedor en ejecución. Solo puede haber una instrucción CMD en un Dockerfile.
* ENTRYPOINT: permite configurar un contenedor que se ejecutará como ejecutable.