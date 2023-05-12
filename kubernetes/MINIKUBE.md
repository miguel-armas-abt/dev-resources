# Minikube
Minikube provee una configuración de clúster ONLY ONE

### Crear/Iniciar el clúster de Kubernetes: 
- `--memory=2816 --cpus=4` Indica la cantidad de memoria y cpus que se asigna al cluster
```shell script
minikube start
```

### Mostrar el estado del clúster: 
```shell script
minikube status
```

### Detener el clúster: 
```shell script
minikube stop
```

### Eliminar el clúster:
```shell script
minikube delete
```

### Habilitar el dashobard de Kubernetes: 
```shell script
minikube dashboard --url
```

### Acceder a un servicio desde fuera del cluster:
Para acceder a un servicio desde fuera del cluster, solicitaremos su URL (dirección IP y puerto) a Minikube
```shell script
minikube service --url <service-name>
```

### Acceder a un servicio desde dentro del cluster:
Para acceder a un servicio desde dentro del clúster utilizaremos la dirección IP del cluster junto con el puerto 
definido en el servicio (`kubectl get services`)
```shell script
minikube ip
```

## Abrir una shell de Minikube
```shell script
minikube ssh
```

## Mostrar los perfiles de minikube disponibles
```shell script
minikube profile list
```
