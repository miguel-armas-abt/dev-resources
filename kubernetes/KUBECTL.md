# KUBERNETES

> 📌 **Notas**
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
> 📌 **Notas**
> <br>El flag `-n` especifica el namespace. Si no se indica, el namespace por defecto es `default`

----

▶️ **Mostrar todos los objetos**
```shell script 
kubectl get all
kubectl get pods --all-namespaces
```

----

▶️ **Mostrar / eliminar / describir objetos**
- **get**
  - Utilice `--all-namespaces` para mostrar los objetos de todos los namespaces
  - Utilice `-o yaml` para formatear la respuesta 
```shell script 
kubectl get <k8s-object>
kubectl delete <k8s-object> <k8s-object-id>
kubectl describe <k8s-object> <k8s-object-id>
```
⚙️ **Nativos de Kubernetes**

| k8s-object        | Objeto                    | Descripción                                                            |
|-------------------|---------------------------|------------------------------------------------------------------------|
| `pods`            | Pod                       | Unidad mínima de ejecución que contiene uno o más contenedores         |
| `service`         | Service                   | Define un punto de acceso a la aplicación                              |
| `deployment`      | Deployment                | Controla la implementación de aplicaciones                             |
| `secret`          | Secret                    | Almacena información sensible de forma segura                          |
| `cm`              | Config Map                | Configura variables de entorno y archivos                              |
| `pv`              | Persistent Volume         | Almacena datos que persisten más allá del ciclo de vida del contenedor |
| `pvc`             | Persistent Volume Claim   | Solicitud de almacenamiento persistente                                |
| `hpa`             | Horizontal Pod Autoscaler | Escala automáticamente los pods basándose en la carga de trabajo       |
| `serviceaccounts` | Service Accounts          | Proporciona identidades para los pods                                  |

⚙️ **Configuraciones en Istio**

| k8s-object        | Objeto           | Descripción                                                                            |
|-------------------|------------------|----------------------------------------------------------------------------------------|
| `destinationrule` | Destination Rule | Define reglas de destino para el enrutamiento de tráfico en Istio                      |
| `envoyfilter`     | Envoy Filter     | Aplica filtros personalizados a los datos que pasan a través del proxy Envoy           |
| `gateways`        | Gateway          | Define una entrada de tráfico externo en la malla de servicios de Istio                |
| `virtualservices` | Virtual Services | Define reglas de enrutamiento para el tráfico dentro de la malla de servicios de Istio |

📋 **Persistent Volume (PV)**:
<br>Para verificar si un `PV` está siendo utilizado por algún `PVC`, puedes describirlo y buscar el campo `Claim`.
- Si `Claim` es el nombre de un PVC, entonces está siendo utilizado.
- Si `Claim` es `<none>`, entonces no está siendo utilizado.

📋 **Persistent Volume Claim (PVC)**
<br> Para verificar si un `PVC` está utilizando algún `PV`, puedes describirlo y buscar el campo `VolumeName`.
- Si `VolumeName` es el nombre de un PV, entonces está utilizándolo.
- Si `VolumeName` es `<nil>`, entonces no está utilizando ninguno.

----

▶️ **Aplicar / Eliminar manifiestos**
- Utilice `-f` para indicar el directorio o nombre de los manifiestos
```shell script 
kubectl apply -f <directory-name>
kubectl delete -f <directory-name>
```
Ejemplos: <br>
`kubectl apply -f ./`
`kubectl delete -f ./deployment.yml`

----

▶️ **Ingresar al sistema de archivos del contenedor asociado a un pod**
- Cambie la shell instalada en los contenedores. `bash`, `sh`
```shell script 
kubectl exec -it <pod-id> -- bash
```

----

▶️ **Mostrar logs del contenedor asociado a un pod**
- Utilice `-f` para seguir los logs en tiempo real. 
```shell script 
kubectl logs -f <pod-id>
```

----

▶️ **Escalar deployments**
```shell script 
kubectl scale deployment <deployment-id> --replicas=3
```

----

▶️ **Historial / Rollback / Estado / Reinicio de un deployment**
- **Historial**: Mostrar el historial de revisiones
- **Rollback**: Revertir el deployment a una revisión anterior
- **Estado**: Mostrar el estado de un despliegue en curso
- **Reinio**: Reiniciar el deployment
```shell script 
kubectl rollout history deployment/<deployment-id>
kubectl rollout undo deployment/<deployment-id> --to-revision=<revision-number>
kubectl rollout status deployment/<deployment-id>
kubectl rollout restart deployment/<deployment-id>
```

----

▶️ **Port forwarding**
```shell script 
kubectl port-forward <pod-id> <local-port>:8080
kubectl port-forward svc/<pod-id> <local-port>:8080
```
