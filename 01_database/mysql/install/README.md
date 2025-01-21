# INSTALACIÓN MYSQL

> ### 📌 Pre-requisitos
> - [Instalar Microsoft Visual C++ Redistributable](https://aka.ms/vs/17/release/vc_redist.x86.exe)

---

[Descargar](https://dev.mysql.com/downloads/mysql/) `Windows (x86, 64-bit), ZIP Archive` y guardar los binarios en la ruta sugerida `C:\dev-environment\mysql\mysql-8.2.0`.

---

💻 Abrir una consola CMD en modo **<u>administrador</u>** e ingresar a los binarios

```
cd bin
```

---

🔓 Inicializar la configuración de MySQL sin una contraseña por defecto para el usuario `root`:
```
mysqld --initialize-insecure
```

---

⚙️ Instalar MySQL80
```
mysqld --install "mysql80"
```

---

▶️ Inciar el servicio:
```
net start mysql80
```

🔑 Inciar sesión sin contraseña:
```
mysql -u root
```

🔐 Establecer contraseña para el usuario `root`:
```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'qwerty';
```

⏹️ Detener el servicio:
```
net stop mysql80
```

👤 Inciar sesión con contraseña:
```
mysql -u root -p"qwerty"
```

---

> 📌 **Nota**: Si necesitas repetir el proceso, asegúrate de eliminar los binarios y descargarlos nuevamente, 
> ya que estos podrían tener configuraciones obsoletas. Además, para desinstalar el servicio de MySQL puedes utilizar:
> ```
> mysqld --remove "mysql80"
> ```
