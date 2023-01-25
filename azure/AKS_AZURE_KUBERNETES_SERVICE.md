# AZURE KUBERNETES SERVICE (AKS)

> Listar clúster de kubernetes del resource group actual. La salida de este comando nos ofrece el nombre de los clústeres
```shell script
az aks list -o table
```

> Cambiar al contexto del clúster de Azure.
>
> Ejemplo: `az aks get-credentials -n aksmabtpe01 -g rgmabt01`
```shell script
az aks get-credentials -n <kubernetes-cluster-name> -g <resource-group-name>
```

> **Nota**: Para validar la conexión a nuestro clúster de Kubernetes podemos intentar utilizar comandos de kubectl. Por ejemplo `kubectl get all`