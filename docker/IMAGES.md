# Imágenes

### Flags
Algunos de los flags más recurrentes al ejecutar comandos de imágenes:
- `--all` es equivalente a `-a` y significa "todas las imágenes almacenadas en el sistema"
- `--force` es equivalente a `-f` y significa "forzar la ejecución"
- `-q` muestra solamente los ID's
- `-t` indica que se definirá un tag

### Construir imagen:
- `.` indica el directorio actual
```shell script
docker build -t <image-name:tag> .
```
Ejemplo:
- `$ docker build -t config-server:0.0.1-SNAPSHOT .`

### Mostrar imágenes: 
```shell script
docker images
```

### Eliminar imagen:
```shell script
docker rmi <image-id> -f
```

### Eliminar todas las imágenes:
```shell script
docker rmi $(docker images -a -q)
```