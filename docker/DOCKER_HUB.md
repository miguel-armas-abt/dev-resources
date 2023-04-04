# Docker Hub

### Autenticar con Docker Hub:
```shell script
docker login
```

### Asociar imagen local al repositorio remoto de imágenes de DockerHub:
```shell script
docker tag <local-image:tag> <username/remote-image:tag>
```
> Ejemplo: `docker tag my-image:0.0.1 miguelarmasabt/my-image:0.0.1`

### Pull a una imagen de Docker Hub:
```shell script
docker pull <username/remote-image:tag>
```

### Push de una imagen hacia Docker Hub:
```shell script
docker push <username/remote-image:tag>
```
> Ejemplo: `docker push miguelarmasabt/my-image:0.0.1`

### Construir un contenedor a partir de una imagen en Docker Hub:
```shell script
docker run -p <local-port>:<internal-port> <username/remote-image:tag>
```
> Ejemplo: `docker run -p 8090:8090 miguelarmasabt/products-image`

### Asignar nuevo tag a imagen
```shell script
docker tag <image-name:local-tag> <username/remote-image:new-tag>
```