## Contenedores
> - Los comandos que requieran el ID del contenedor reconocen el contenedor a partir de los 3 primeros dígitos.

> Construir nuevo contenedor:
```shell script
docker run -p <local-port>:<internal-port> --name <container-name> --network <network-name> <image-name>
```

> Eliminar contenedor:
```shell script
docker rm <container-id>
```

> Iniciar un contenedor previamente detenido:
```shell script
docker start <container-id>
```

> Detener un contenedor previamente iniciado:
```shell script
docker stop <container-id>
```

> Listar los contenedores activos:
```shell script
docker container ls
```
```shell script
docker ps 
```

> Listar todos los contenedores (activos y detenidos):
```shell script
docker ps -a
```

> Eliminar los contenedores detenidos y los volúmenes y redes no usados:
```shell script
docker system prune
```

> Ver lista de comandos para contenedores:
```shell script
docker container --help
```

> Ver logs:
```shell script
docker logs -f <container-name>
```