# QUARKUS - INYECCIÓN DE DEPENDENCIAS (DI)

[← Ir a Quarkus](./../README.md) <br>

Quarkus al ser un producto compatible de [Microprofile](./../../jakartaee-microprofile/java-community-process/README.md)
implementa la especificación [CDI](./../../jakartaee-microprofile/context-dependency-injection/README.md).

## Arc
- Quarkus utiliza su propia implementación ligera de CDI llamada Arc.
- Arc está diseñado para ser rápido y eficiente en términos de memoria (crítico en microservicios y nube).
- Está optimizado para el modelo de programación reactivo y tiempos de arranque rápidos.

![DI](./images/cdi-jakarta-ee.png)

