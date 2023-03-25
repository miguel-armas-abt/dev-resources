Minikube provee una configuración de clúster Only one

> Iniciar el clúster de Kubernetes: 
```shell script
minikube start
```

> Mostrar el estado del clúster de Kubernete: 
```shell script
minikube status
```

> Detener el clúster de Kubernetes: 
```shell script
minikube stop
```

> Habilitar el dashobard de Kubernetes: 
```shell script
minikube dashboard --url
```

> Para acceder a un servicio desde fuera del clúster (Por ejemplo, acceder a PgAdmin desde el navegador) utilizaremos la URL generada por Docker Desktop 'minikube service --url <service-name>'

> Para acceder a un servicio desde dentro del clúster (Por ejemplo, generar una conexión al servicio de PostgreSQL desde PgAdmin, ambos dentro del clúster) utilizaremos la IP 'minikube ip' y el puerto del servicio optenido con 'kubectl get services'

> Mostrar la IP del clúster de Kubernetes: 
```shell script
minikube ip
```

> Mostrar la URL de un servicio en el clúster de Kubernetes: 
```shell script
minikube service --url <service-name>
```
