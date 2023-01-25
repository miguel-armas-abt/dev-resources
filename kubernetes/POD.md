# POD
> - Unidad de cálculo más pequeña
> - Agrupa a uno o más contenedores
> - Los contenedores pueden compartir red

> Las siguientes especificaciones corresponden a **pod.yaml**
```javascript
apiVersion: v1 
kind: Pod 
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

> Listar pods: 
```shell script
kubectl get pods
```

> Definir pod. Si no existe, lo crea y si existe lo actualiza: 
```shell script
kubectl apply -f directory/pod.yaml
```

> Visualizar logs del pod:
>
> Ejemplo: `kubectl logs api-pod`
```shell script
kubectl logs <pod-name>
```

> Eliminar pod:
>
> Ejemplo: `kubectl delete pod api-pod`
```shell script
kubectl delete pod <pod-name>
```
```shell script
kubectl delete pod <pod-id>
```
