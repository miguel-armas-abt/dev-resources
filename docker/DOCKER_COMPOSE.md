> Ejecutar el fichero docker-compose.yaml:
```shell script
docker compose up -d
```

> Forzar la ejecución del fichero docker-compose.yaml
```shell script
docker compose up -d --force-recreate
```

> Iniciar los servicios que no están iniciados
```shell script
docker-compose start
```

> Detener los servicios que están iniciados
```shell script
docker-compose stop 
```

> Ejecutar solo un miembro del docker compose
>
> Ejemplo: `docker-compose -f docker-compose.yml up -d keycloak-server`
```shell script
docker-compose -f docker-compose.yml up -d <component-name>
```