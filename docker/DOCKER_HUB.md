## Docker Hub

> Autenticar con Docker Hub:
```shell script
docker login
```

> Asociar imagen local al repositorio remoto de imágenes de DockerHub:
>
> Ejemplo: `docker tag my-image:0.0.1 miguelarmasabt/my-image:0.0.1`
```shell script
docker tag <local-image:tag> <username/remote-image:tag>
```

> - Hacer pull a imagen de Docker Hub:
```shell script
docker pull <username/remote-image:tag>
```

> Hacer push a imagen hacia Docker Hub:
>
> Ejemplo: `docker push miguelarmasabt/my-image:0.0.1`
```shell script
docker push <username/remote-image:tag>
```

> **Nota**: Para construir un contenedor desde una imagen propia en Docker Hub se sugiere eliminar nuestra imagen local para evitar algún cruce de referencias.

> Eliminar imagen local asociada al repositorio remoto de imágenes de DockerHub:
>
> Ejemplo: `docker rmi my-image::0.0.1 miguelarmasabt/my-image:0.0.1`
```shell script
docker rmi <local-image:tag> <username/remote-image:tag>
```

> Construir contenedor a partir de una imagen en Docker Hub:
>
> Ejemplo: `docker run -p 8090:8090 miguelarmasabt/products-image`
```shell script
docker run -p <local-port>:<internal-port> <username/remote-image:tag>
```

> Asignar nuevo tag a imagen
```shell script
docker tag <image-name:local-tag> <username/remote-image:new-tag>
```