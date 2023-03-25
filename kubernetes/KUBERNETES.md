# KUBERNETES
> - Cada elemento de Kubernetes es un objeto
> - Un objeto representa un estado deseado (características deseadas)
> - YAML es la forma de definir el estado del objeto
> - Los proveedores de la nube ofrecen Kubernetes administrados

> Cambiar de contexto. Para cambiar entre el contexto de Docker Desktop o Minikube.
>
> Ejemplo: `kubectl config use-context docker-desktop`
```shell script
kubectl config get-contexts
kubectl config use-context <context-name>
```

> Obtener versión de API Server: 
```shell script
kubectl api-versions
```

> Desplegar. Ejecutar los archivos pod.yml, deployment.yml, service.yml ubicados en el directorio directory-deploy/: 
```shell script
kubectl apply -f directory-deploy/
```

> Listar todo (pods, deployments y services): 
```shell script
kubectl get all
```

> Eliminar cambios realizados en el despliegue: 
```shell script
kubectl delete -f directory-deploy/
```
