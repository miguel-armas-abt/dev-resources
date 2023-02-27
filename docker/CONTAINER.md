## Contenedores
> Construir nuevo contenedor:
> - El flag --rm indica que se eliminará el contenedor cuando se detenga
> - El flag -d indica que se ejecutará el contenedor en segundo plano
>
> Ejemplo: `$ docker run --rm -p 8093:8093 --name my-container my-image:0.0.1`
```shell script
docker run --rm -p <local-port>:<internal-port> --name <container-name> --network <network-name> <image-name:tag>
```

> Eliminar contenedor:
```shell script
docker rm <container-id || container-name>
```

> Eliminar todos los contenedores detenidos:
> - El flag `--all` indica la eliminación de imágenes, contenedores, volúmenes y redes que no estén siendo utilizadas 
```shell script
docker system prune --all
```

> Iniciar un contenedor previamente detenido:
```shell script
docker start <container-id || container-name>
```

> Detener un contenedor previamente iniciado:
```shell script
docker stop <container-id || container-name>
```

> Detener todos los contenedores:
```shell script
docker stop $(docker ps -a -q)
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

> Ver lista de comandos para contenedores:
```shell script
docker container --help
```

> Ver logs:
```shell script
docker logs -f <container-id || container-name>
```

> Ver métricas de consumo:
```shell script
docker stats
```