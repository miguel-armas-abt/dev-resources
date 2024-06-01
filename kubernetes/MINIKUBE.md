# MINIKUBE
Minikube provee una configuración de clúster ONLY ONE

----

▶️ **Iniciar / Mostrar estado / Detener / Eliminar el clúster de Kubernetes**
```shell script 
minikube start --memory=2816 --cpus=4
minikube status
minikube stop
minikube delete
```

----

📈 **Habilitar el dashobard de Kubernetes**
```shell script 
minikube dashboard --url
```

----

🔀 **Port forwarding de un servicio**
<br>Permite acceder desde nuestro entorno local a los servicios disponibles en el clúster k8s de Minikube
```shell script 
minikube service --url <service-name>
```

----

🔀 **Apuntar a un servicio dentro del clúster**
<br>Para acceder a un servicio desde dentro del clúster podemos utilizar la dirección IP del cluster de Minikube junto 
con el puerto de escucha definido para el servicio (`kubectl get services`)
```shell script 
minikube ip
```

----

▶️ **Abrir shell de Minikube**
```shell script
minikube ssh
```

----

▶️ **Mostrar los perfiles de minikube disponibles**
```shell script
minikube profile list
```

----

▶️ **Iniciar el cluster de Minikube**
- Para especificar los recursos asignados a Minukube, puede indicar `--memory=2816 --cpus=4`.
- Utilice el contexto default de Docker.
```shell script
 docker context use default
 minikube start
```

----

▶️ **Acceder al Docker de Minikube**
- Windows:
```shell script 
 Invoke-Expression ((minikube docker-env) -join "`n")
```

- Unix:
```shell script 
 eval $(minikube docker-env --shell bash)
```
