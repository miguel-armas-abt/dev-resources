
 ### Instalar MySQL
 Descargar `Windows (x86, 64-bit), ZIP Archive` y reservar los binarios.
 <br>**Ruta**: `C:\dev-environment\mysql\mysql-8.2.0`
 <br>https://dev.mysql.com/downloads/mysql/

 Ingresar a los binarios e instalar:
 ```
 cd bin
 mysqld --initialize
 mysqld --install "mysql80"
 ```
 Inciar el servidor:
 ```
 net start mysql80
 ```
 Cambiar de password:
 ```
 ALTER USER 'root'@'localhost' IDENTIFIED BY 'qwerty';
 ```
 Inciar sesión:
 ```
 mysql -u root -p"qwerty"
 ```
