# Contenedores
- Los contenedores pueden referenciarse a través de su nombre o ID.

### Flags
Algunos de los flags más recurrentes al ejecutar comandos de contenedores:
- `--all` es equivalente a `-a` y significa "todos los contenedores (detenidos y en ejecución)"
- `--force` es equivalente a `-f` y significa "forzar la ejecución"
- `-q` muestra solamente los ID's

### Construir nuevo contenedor:
- `--rm` indica que se eliminará el contenedor cuando se detenga
- `-d` indica que se ejecutará el contenedor en segundo plano
```shell script
docker run --rm -p <local-port>:<internal-port> --name <container-name> --network <network-name> <image-name:tag>
```
Ejemplos:
- `$ docker run --rm -p 8093:8093 --name my-container my-image:0.0.1`

### Mostrar logs:
- `-f` indica que se hará follow en primer plano
```shell script
docker logs -f <container-id>
```

### Detener un contenedor previamente iniciado:
```shell script
docker stop <container-id>
```

### Iniciar un contenedor previamente detenido:
```shell script
docker start <container-id>
```

### Eliminar contenedor:
```shell script
docker rm <container-id>
```

### Detener todos los contenedores:
```shell script
docker stop $(docker ps -a -q)
```

### Eliminar los contenedores detenidos:
```shell script
docker container prune -f -a
```

### Mostrar los contenedores:
```shell script
docker ps -a
docker ps -a --format "table {{.ID}}\t{{.Names}}\t{{.Status}}"
```

### Mostrar comandos para contenedores:
```shell script
docker container --help
```

### Mostrar métricas de consumo:
```shell script
docker stats
```

### Ingresar al sistema de archivos de un contenedor en ejecución:
- `it` habilita la opción de "interactivo" y asigna una terminal TTY para la sesión
- `sh` comando que se ejecutará dentro del contenedor para abrir una sesión de shell
- `bash` comando que se ejecutará dentro del contenedor para abrir una sesión de bash
```shell script
docker exec -it <container-id> bash
```

### Inspeccionar las características del contenedor:
```shell script
docker container inspect <container-id>
```

### Agregar un contenedor a la red de otro:
```shell script
docker network connect <container1-id> <container2-id>
```