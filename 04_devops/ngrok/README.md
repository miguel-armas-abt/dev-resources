# NGROK

Ngrok permite realizar forward de una URL local hacia una URL pública.
- Ingrese a https://ngrok.com/ y haga login
- Descargue el archivo `ngrok.exe`
- Ejecute solo la primera vez el comando provisto por Ngrok para autenticarse.
```shell script 
 ngrok config add-authtoken <ngrok-auth-token>
```
- Realice forward de su URL local.
```shell script 
 ngrok http http://localhost:8080
```