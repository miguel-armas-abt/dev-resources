# AZURE CONTAINER REGISTRY (ACR)
> En local tenemos instalado Docker y podemos construir una imagen con el comando `docker build ...`. Sin embargo, en cloud no contamos con la herramienta Docker, pero en su lugar el cloud provider (Azure) nos ofrece una línea de comandos para hacerlo, Azure Container Registry (ACR).

> Listar los contenedores registry. La salida de este comando nos ofrece el nombre de los contenedores 
```shell script
az acr list -o table
```

> Construir el contenedor (desde el directorio donde está ubicado Dockerfile) y registrarlo en ACR
>
> Ejemplo: `az acr build ./ --image my-image --registry acrmabt01`
```shell script
az acr build <dockerfile-directory> --image <image-name> --registry <registry-name>
```

> **Nota:** Podemos validar que el contenedor se registró en el ACR yendo a la sección repositories del registry service que creamos en nuestro resource group.