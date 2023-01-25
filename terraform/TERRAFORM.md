# TERRAFORM 
> - Terraform es una herramienta open source para aprovisionar infraestructura mediante código declarativo.
> - Permite automatizar y gestionar la infraestructura informática necesaria para desplegar plataformas y servicios sobre ella.

## Pasos para aprovisionar una infraestructura en AZURE
> - Ingresar al bash del cloud provider (Azure)
> - Clonar nuestro repositorio /terraform en este espacio y acceder a ella `cd /terraform`
> - En este directorio encontraremos los siguientes ficheros:
>   - **main.tf**: Define los recursos a aprovisionar (container registry, cluster aks, net)
>   - **locals.tf**: Define los datos que utiliza main.tf
> - Ejecutamos los siguientes comandos para realizar el aprovisionamiento:
```shell script
terraform init
```
```shell script
terraform apply
```

## Otros comandos
```shell script
terraform validate
```
```shell script
terraform plan
```

> Eliminar los camios realizados por `terraform apply`
```shell script
terraform destroy 
```
