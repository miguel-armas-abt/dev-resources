# DOCKER
> **Imagen:** Una imagen es la composición de un Dockerfile y nuestra aplicación en estado compilado

> **Container:** Un contenedor es una imagen docker, es estado de ejecución

> **Engine:** Es lo que utiliza el demonio de docker que está instalado en el host para poder comunicarse con la red y los volúmenes del host

> **Registry:** Es donde almacenamos las imágenes de docker para que puedan ser distribuidas

### Eliminar todos los recursos que no estén siendo utilizados:
Implica la eliminación de imágenes, contenedores, volúmenes y redes
- `--all` indica todos los recursos, incluyendo los que están actualmente en uso
```shell script
docker system prune --all
```

### Configurar Docker Desktop
> Para especificar los recursos asignados a Docker Desktop, cree un archivo `.wslconfig` en la ruta
> `C:\Users\<username>\`, agregue el siguiente contenido en dependencia de los recursos de su entorno y reinicie Docker Desktop.
> ```javascript
> [wsl2]
> memory=3072MB
> processors=5
> ```