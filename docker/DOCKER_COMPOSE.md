# DOCKER COMPOSE

## Compatibilidad
Docker Compose requiere ser compatible con el Docker Engine y Docker YML file.
<https://docs.docker.com/compose/compose-file/compose-versioning/>

## Service
Un "service" representa un conjunto de configuraciones que definen cómo ejecutar uno o más contenedores de Docker.

## Comandos

### Flags
Algunos de los flags más recurrentes al ejecutar comandos de Docker Compose:
> - `-f docker-compose-custom.yml` permite ejecutar un archivo .yml diferente a docker-compose.yml
> - `-d` activa la ejecución en segundo plano

### Iniciar los servicios definidos en la orquestación:
- `--force-recreate` fuerza la recreación de los servicios
- Para iniciar un servicio específico podemos agregar su nombre al final del comando
- `--scale <service-name>=<replicas-number>` escala un servicio con una cantidad de réplicas
```shell script
docker-compose up
```
> Ejemplo: `docker-compose up --scale  billingapp-front=3 -d --force-recreate`

### Iniciar los servicios que aún no han iniciado:
```shell script
docker-compose start
```

### Eliminar los servicios definidos en la orquestación:
```shell script
docker-compose down
```

### Detener todos los servicios de la orquestación:
```shell script
docker-compose stop 
```

### Pull a las imágenes requeridas en la orquestación:
```shell script
docker-compose pull
```

### Construir las imágenes definidas en la orquestación:
```shell script
docker-compose build
```

### Obtener versión:
```shell script
docker-compose --version
docker compose version
```

