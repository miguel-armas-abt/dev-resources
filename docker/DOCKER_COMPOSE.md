> Versión de docker-compose:
```shell script
docker-compose --version
```
```shell script
docker compose version
```

> Hacer pull a las imágenes requeridas en la orquestación:
```shell script
docker-compose pull
```

> Construir las imágenes definidas en la orquestación:
```shell script
docker-compose build
```

> Inicializar los contenedores de los servicios de la orquestación:
> - El flag `-f` <yml-file> permite ejecutar un archivo diferente a docker-compose.yml
> - El flag `-d` activa la ejeución en segundo plano
> - El flag `--force-recreate` fuerza la inicialización de los contenedores
```shell script
docker-compose -f <yml-file> up -d --force-recreate
```

> Iniciar los contenedores de la orquestación que aún no han iniciado:
```shell script
docker-compose start
```

> Detener todos los contenedores de la orquestación:
```shell script
docker-compose stop 
```

> Ejecutar solo un contenedor de los definidos en la orquestación:
>
> Ejemplo: `docker-compose -f docker-compose.yml up -d keycloak-server`
```shell script
docker-compose -f docker-compose.yml up -d <component-name>
```

> Al usar Docker Compose debemos considerar la compatibilidad entre Docker Engine, Docker Compose y Docker YML file.
> `https://docs.docker.com/compose/compose-file/compose-versioning/`

