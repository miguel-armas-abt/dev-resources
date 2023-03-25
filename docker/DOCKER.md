# DOCKER
> **Imagen:** Una imagen es la composición de un Dockerfile y nuestra aplicación en estado compilado

> **Container:** Un contenedor es una imagen docker, es estado de ejecución

> **Engine:** Es lo que utiliza el demonio de docker que está instalado en el host para poder comunicarse con la red y los volúmenes del host

> **Registry:** Es donde almacenamos las imágenes de docker para que puedan ser distribuidas

> Versión de Docker: 
```shell script
docker --version
```

> Acceder a un contenedor en modo bash: 
```shell script
docker exec -it <container-name> /bin/bash
```