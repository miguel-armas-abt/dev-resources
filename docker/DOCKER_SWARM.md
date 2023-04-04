# Docker Swarm

## Stack
Un "stack" representa un conjunto de configuraciones que definen cómo ejecutar un grupo de contenedores de Docker.

## Comandos

### Flags
Algunos de los flags más recurrentes al ejecutar comandos de Docker Compose:
> - `-c` permite ejecutar un archivo .yml diferente a docker-swarm.yml 

### Mostrar información de Docker: 
```shell script
docker info
```

### Activar Docker Swarm: 
```shell script
docker swarm init
```

### Desconectar nodo del clúster de Docker Swarm (Desactivar):
```shell script
docker swarm leave --force
```

### Iniciar los servicios definidos en la orquestación (stack):
- Para iniciar un servicio específico podemos agregar su nombre al final del comando
```shell script
docker stack deploy -c <yml-file>
```

### Mostrar todos los servicios desplegados:
```shell script
docker service ls
```

### Mostrar los servicios desplegados en un stack específico:
```shell script
docker stack ps <stack-name>
```

### Detener el stack:
```shell script
docker stack rm <stack-name>
```