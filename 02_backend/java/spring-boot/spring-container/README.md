# CONTENEDOR DE SPRING

[← Ir a Spring Boot](./../README.md) <br>

## Tipos de contenedores IoC

- `BeanFactory`: Contenedor simple con soporte básico para DI.
- `ApplicationContext`: Contenedor que extiende `BeanFactory` e incluye capacidades adicionales.
  - Soporte para resolución de mensajes y `i18n`.
  - Soporte para publicar y suscribir eventos dentro de la aplicación.
  - Carga de beans desde archivos de configuración o a través de `@Configuration`.
  - Integración con Programación Orientada a Aspectos (AOP).

En la práctica `ApplicationContext` es la elección predeterminada debido a su robustez, mientras que `BeanFactory` se 
utiliza cuando se requiere un contenedor extremadamente ligero (applets, apps moviles, etc).