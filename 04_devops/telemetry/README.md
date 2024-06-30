# TELEMETRÍA Y OBSERVABILIDAD

> **Telemetría** <br>
> Se refiere a la recopilación, transmisión y análisis de datos sobre el rendimiento y comportamiento de las aplicaciones.
> La telemetría incluye:
> - **Métricas**: Datos cuantitativos sobre el rendimiento del sistema, como latencia, uso de CPU y memoria.
> - **Logs**: Registros generados por la aplicación, como errores, advertencias e informativos.
> - **Trazas**: Información sobre la propagación de las solicitudes a través de diferentes servicios.
> 
> La telemetría proporciona los datos necesarios para configurar monitoreo y alertas que informen a los operadores sobre 
> problemas antes que afecten a los usuarios.

> **Observabilidad** <br>
> Capacidad de entender lo que está sucediendo dentro de un sistema basado en los datos de telemetría.

| Herramienta                          | Utilidad                                                                                             |
|--------------------------------------|------------------------------------------------------------------------------------------------------|
| [Prometheus](./prometheus/README.md) | Brinda métricas de rendimiento y estado de aplicaciones, como uso de CPU, RAM, tasas de error, etc.  |
| [Zipkin](./zipkin/README.md)         | Brinda visibilidad sobre la propagación de una solicitud a través de múltiples servicios.            |
| Loki                                 | Permite almacenar y consultar Logs.                                                                  |
| [Grafana](./grafana/README.md)       | Brinda dashboards personalizados basados en las métricas de Prometheus, Loki u otra fuente de datos. |

**Nota**: `OpenTelemetry` es una especificación que proporciona una API y SDKs independientes del lenguaje para la instrumentación de trazas, métricas y logs.
