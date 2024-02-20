# KUBERNETES

## General

> **Mostrar la configuración del clúster (Minikube)**
> ```shell script 
> kubectl config view 
> ```

> **Mostrar nodos**
> ```shell script 
> kubectl get nodes 
> ```

> **Mostrar información del clúster**
> ```shell script 
> kubectl cluster-info
> ```

> **Mostrar la versión del API Server**
> ```shell script 
> kubectl api-versions
> ```

> **Mostrar / Cambiar contexto o aks**
> ```shell script 
> kubectl config get-contexts
> kubectl config use-context <context-name>
> ```
> Ejemplos:<br>
> `kubectl config use-context minikube`
> `kubectl config use-context askeu2008bbqdev02`

## Namespace
Los siguientes comandos requieren el flag `-n` para especificar el namespace. Si no se indica, por defecto es `default`.

> **Aplicar / Eliminar manifiestos**
> - `-f` indica el directorio o nombre de los manifiestos
> ```shell script 
> kubectl apply -f <directory-name>
> kubectl delete -f <directory-name>
> ```
> Ejemplos: <br>
> `kubectl apply -f ./`
> `kubectl delete -f ./deployment.yml`

> **Mostrar todos los objetos**
> ```shell script 
> kubectl get all
> ```

> **Mostrar / eliminar / describir objetos**
> <br> **k8s-object**: `pod` | `service` | `deployment` | `secret` | `cm`: config map | `pv`: persistent volume | `pvc`: persistent volume claim 
> ```shell script 
> kubectl get <k8s-object>
> kubectl delete <k8s-object> <k8s-object-id>
> kubectl describe <k8s-object> <k8s-object-id>
> ```
> > 📋 **Persistent Volume (PV)**: 
> > <br>Para verificar si un `PV` está siendo utilizado por algún `PVC`, puedes describirlo y buscar el campo `Claim`.
> > - Si `Claim` es el nombre de un `PVC`, entonces está siendo utilizado.
> > - Si `Claim` es `<none>`, entonces no está siendo utilizado.
>
> > 📋 **Persistent Volume Claim (PVC)**
> > <br> Para verificar si un `PVC` está utilizando algún `PV`, puedes describirlo y buscar el campo `VolumeName`.
> > - Si `VolumeName` es el nombre de un `PV`, entonces está utilizándolo.
> > - Si `VolumeName` es `<nil>`, entonces no está utilizando ninguno.

> **Ingresar al sistema de archivos del contenedor asociado a un pod**
> - Puede cambiar el flag `bash` por `sh` de acuerdo a la shell instalada en los contenedores.
> ```shell script 
> kubectl exec -it <pod-id> -- bash
> ```

> **Mostrar logs del contenedor asociado a un pod**
> ```shell script 
> kubectl logs <pod-id>
> ```

> **Escalar deployments**
> ```shell script 
> kubectl scale deployment <deployment-id> --replicas=3
> ```


