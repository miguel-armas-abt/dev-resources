# KUBERNETES

> 📋 **Notas**
> - **Clúster**: Minikube, AKS

## Comandos generales

▶️ **Mostrar información del clúster**
```shell script 
kubectl cluster-info
```

----

▶️ **Mostrar la configuración del clúster**
```shell script 
kubectl config view 
```

----

▶️ **Mostrar nodos**
```shell script 
kubectl get nodes 
```

----

▶️ **Mostrar la versión del API Server**
```shell script 
kubectl api-versions
```

----

▶️ **Mostrar / Cambiar contexto**
```shell script 
kubectl config get-contexts
kubectl config use-context <context-name>
```
Ejemplos:<br>
`kubectl config use-context minikube`
`kubectl config use-context askeu2008bbqdev02`

----

## Comandos en un namespace
> 📋 **Notas**
> <br>El flag `-n` especifica el namespace. Si no se indica, el namespace por defecto es `default`

----

▶️ **Aplicar / Eliminar manifiestos**
- `-f` indica el directorio o nombre de los manifiestos
```shell script 
kubectl apply -f <directory-name>
kubectl delete -f <directory-name>
```
Ejemplos: <br>
`kubectl apply -f ./`
`kubectl delete -f ./deployment.yml`

----

▶️ **Mostrar todos los objetos**
```shell script 
kubectl get all
```

----

▶️ **Mostrar / eliminar / describir objetos**
```shell script 
kubectl get <k8s-object>
kubectl delete <k8s-object> <k8s-object-id>
kubectl describe <k8s-object> <k8s-object-id>
```

| k8s-object   | descripción             |
|--------------|-------------------------|
| `pod`        | Pod                     |
| `service`    | Service                 |
| `deployment` | Deployment              |
| `secret`     | Secret                  |
| `cm`         | Config Map              |
| `pv`         | Persistent Volume       |
| `pvc`        | Persistent Volume Claim |

📋 **Persistent Volume (PV)**:
<br>Para verificar si un `PV` está siendo utilizado por algún `PVC`, puedes describirlo y buscar el campo `Claim`.
- Si `Claim` es el nombre de un PVC, entonces está siendo utilizado.
- Si `Claim` es `<none>`, entonces no está siendo utilizado.

📋 **Persistent Volume Claim (PVC)**
<br> Para verificar si un `PVC` está utilizando algún `PV`, puedes describirlo y buscar el campo `VolumeName`.
- Si `VolumeName` es el nombre de un PV, entonces está utilizándolo.
- Si `VolumeName` es `<nil>`, entonces no está utilizando ninguno.

----

▶️ **Ingresar al sistema de archivos del contenedor asociado a un pod**
- Cambie la shell instalada en los contenedores. `bash`, `sh`
```shell script 
kubectl exec -it <pod-id> -- bash
```

----

▶️ **Mostrar logs del contenedor asociado a un pod**
```shell script 
kubectl logs <pod-id>
```

----

▶️ **Escalar deployments**
```shell script 
kubectl scale deployment <deployment-id> --replicas=3
```

