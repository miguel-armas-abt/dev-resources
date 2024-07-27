# EJECUTAR APLICACIÓN QUARKUS

[← Ir a Quarkus](./../README.md) <br>

## IntelliJ IDEA
- Instale el plugin `Quarkus Run Configs`

![DI](./images/quarkus-run-configs.png)

- Seleccione `Edit configuration`

![DI](./images/edit-configurations.png)

- Agregue una nueva configuración para Quarkus con Maven

![DI](./images/quarkus-maven-configuration.png)

- Configure el proyecto
```
clean compile quarkus:dev
```

![DI](./images/quarkus-configuration.png)