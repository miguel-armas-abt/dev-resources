# SERVICE
> - Expone pods sin utilizar una dirección IP para hacerlo, a través de labels y selectors
> - Representa un balanceador de carga

> Las siguientes especificaciones corresponden a **service.yaml**
```javascript
kind: Service 
apiVersion: v1 
metadata: 
 name: api-service 
spec: 
 type: LoadBalancer 
 selector: 
   app: api-app 
 ports: 
   - protocol: TCP 
     port: 80 
     targetPort: 8090 
```

> Definir service. Si no existe, lo crea y si existe lo actualiza: 
```shell script
kubectl apply -f directory/service.yaml
```

> Listar servicios: 
```shell script
kubectl get svc
```
