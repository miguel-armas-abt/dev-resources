## Docker Hub

> Autenticar con Docker Hub:
```shell script
docker login
```

> Asociar imagen local al repositorio remoto de imágenes de DockerHub:
>
> Ejemplo: `docker tag my-image:v1 miguelarmasabt/my-image`
```shell script
docker tag <local-image-name> <dockerhub-image-repository>
```

> Pushear imagen a Docker Hub:
>
> Ejemplo: `docker push miguelarmasabt/my-image`
```shell script
docker push <dockerhub-image-repository>
```

> **Nota**: Para construir un contenedor desde una imagen propia en Docker Hub se sugiere eliminar nuestra imagen local para evitar algún cruce de referencias.

> Eliminar imagen local asociada al repositorio remoto de imágenes de DockerHub:
>
> Ejemplo: `docker rmi my-image:v1 miguelarmasabt/my-image`
```shell script
docker rmi <local-image-name>:<tag> <dockerhub-image-repository>
```

> Construir contenedor a partir de una imagen en Docker Hub:
>
> Ejemplo: `docker run -p 8090:8090 miguelarmasabt/products-image`
```shell script
docker run -p <local-port>:<internal-port> <dockerhub-image-repository>
```