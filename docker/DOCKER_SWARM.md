## Docker Swarm

> Información de Docker: 
```shell script
docker info
```

> Activar Docker Swarm: 
```shell script
docker swarm init
```

> Desconectar nodo del clúster de Docker Swarm (Desactivar):
```shell script
docker swarm leave --force
```

> Iniciar los contenedores de los servicios de la orquestación (stack): 
> - El flag `-c` <yml-file> permite identificar un archivo yml
> - El nombre del stack se agrega como prefijo a los nombres de los contenedores que hacen parte del stack
```shell script
docker stack deploy -c <yml-file> <stack-name>
```

> Mostrar los contenedores de los servicios desplegados:
```shell script
docker service ls
```

> Mostrar los contenedores de los servicios desplegados en un stack particular:
```shell script
docker stack ps <stack-name>
```

> Detener el stack:
```shell script
docker stack rm <stack-name>
```