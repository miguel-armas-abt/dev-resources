# KUBERNETES

> **Mostrar nodos**
> ```shell script 
> kubectl get nodes 
> ```

> **Mostrar/Cambiar contexto**
> ```shell script 
> kubectl config get-contexts
> kubectl config use-context <context-name>
> ```
> Ejemplo:
> `kubectl config use-context minikube`

> **Mostrar información del clúster**
> ```shell script 
> kubectl cluster-info
> ```

> **Mostrar la versión del API Server**
> ```shell script 
> kubectl api-versions
> ```

> **Aplicar manifiestos**
> - `-f` indica el directorio y/o nombre de el/los manifiesto(s)
> ```shell script 
> kubectl apply -f <directory-name>
> ```
> Ejemplo:
> - `kubectl apply -f ./`
> - `kubectl apply -f ./deployment.yml`

> **Eliminar manifiestos**
> ```shell script 
> kubectl delete -f <directory-name>
> ```
> Ejemplo:
> - `kubectl delete -f ./`
> - `kubectl delete -f ./deployment.yml`


### Mostrar todos los objetos
Muestra pods, deployments y services 
```shell script
kubectl get all
```

### Mostrar/eliminar/describir Persistent Volume (PV):
- Para verificar si un PV está siendo utilizado por algún PVC, puedes describirlo y buscar el campo Claim
  - Si el valor del campo Claim es el nombre de un PVC, significa que el PV está siendo utilizado por ese PVC
  - Si el valor del campo Claim es `<none>`, significa que el PV no está siendo utilizado por ningún PVC
```shell script
kubectl get pv
kubectl delete pv <pv-name>
kubectl describe pv <pv-name>
```

### Mostrar/eliminar/describir Persistent Volume Claims (PVC):
- Para verificar si un PVC está utilizando algún PV, puedes describirlo y buscar el campo VolumeName
  - Si el valor del campo VolumeName es el nombre de un PV, significa que el PVC está utilizando ese PV
  - Si el valor del campo VolumeName es `<nil>`, significa que el PVC no está utilizando ningún PV
```shell script
kubectl get pvc
kubectl delete pvc <pvc-name>
kubectl describe pvc <pvc-name>
```

### Mostrar/eliminar/describir Config Maps (CM):
```shell script
kubectl get cm
kubectl delete cm <cm-name>
kubectl describe cm <cm-name>
```

### Mostrar/eliminar/describir Secrets:
```shell script
kubectl get secrets
kubectl delete secret <secret-name>
kubectl describe secret <secret-name>
```

### Mostrar/eliminar/describir Pods:
```shell script
kubectl get pods
kubectl delete pod <pod-id>
kubectl describe pod <pod-id>
```

> **Ingresar al sistema de archivos del contenedor asociado a un pod**
> - Puede cambiar el flag `bash` por `sh` de acuerdo a la shell instalada en los contenedores.
> ```shell script 
> kubectl exec -it <pod-id> -- bash
> ```

### Mostrar logs del contenedor asociado a un pod:
```shell script
kubectl logs <pod-id>
```

### Mostrar/eliminar/describir Services:
```shell script
kubectl get svc
kubectl delete svc <service-name>
kubectl describe svc <service-name>
```

### Mostrar/eliminar/describir/escalar Deployments:
```shell script
kubectl get deployments
kubectl delete deployment <deployment-name>
kubectl describe deployment <deployment-name>
kubectl scale deployment <deployment-name> --replicas=3
```

### Ver la configuración del clúster (Minikube):
```shell script
kubectl config view
```
