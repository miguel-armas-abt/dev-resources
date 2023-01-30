## Imágenes
> Construir imagen:
>
> Ejemplo: `$ docker build -t config-server:v1 .`
> - El punto (.) indica el directorio donde se ubica el .jar
```shell script
docker build -t <image-name>:<tag>
```

> Listar imágenes: 
```shell script
docker images
```
```shell script
docker image ls
```

> Eliminar imagen: 
```shell script
docker rmi -f <image-name>:<tag> 
```