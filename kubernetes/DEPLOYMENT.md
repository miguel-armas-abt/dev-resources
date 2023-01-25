# DEPLOYMENT
> - Reconoce que los pods son mortales (reemplaza automáticamente a los pods muertos)
> - Puede generar réplicas del pod
> - Permite escalar
> - Define cómo desplegar
- Mantiene el estado del kubernetes

> Las siguientes especificaciones corresponden a **deployment.yaml**
```javascript
apiVersion: apps/v1 
kind: Deployment 
metadata: 
 name: api-deployment 
 labels: 
   app: api-app 
spec: 
 replicas: 5 
 selector: 
   matchLabels: 
     app: api-app 
 template: 
   metadata: 
     name: api-pod 
     labels: 
       app: api-app 
   spec: 
     containers: 
       - name: api-container 
         image: miguelarmasabt/my-image 
         ports: 
           - containerPort: 8090 
```

> Definir deployment. Si no existe, lo crea y si existe lo actualiza: 
```shell script
kubectl apply -f directory/deployment.yaml
```

> Escalar: 
```shell script
kubectl scale deployment <deployment-name> --replicas=3
```