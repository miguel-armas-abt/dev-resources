## Imágenes
> Construir imagen:
> - El punto (.) indica el directorio donde nos ubicamos
> - El flag --no-cache indica que no se utilizará cache de construcciones anteriores
>
> Ejemplo: `$ docker build -t config-server:v1 .`
>
> Ejemplo: `$ docker build -t billingapp:prod --no-cache --build-arg JAR_FILE=target/*.jar .`

```shell script
docker build -t <image-name:tag> .
```
```shell script
docker build -t <image-name:tag> --no-cache --build-arg <ARG-NAME>=<arg-value> .
```

> Listar imágenes: 
```shell script
docker images
```
```shell script
docker image ls
```

> Eliminar imagen: 
> - El flag --force indica que se forzará la eliminación de la imagen
```shell script
docker image rm <image-name:tag || image-id> --force
```
```shell script
docker rmi -f <image-name:tag || image-id>
```

> Eliminar todas las imágenes: 
```shell script
docker rmi $(docker images -a -q)
```