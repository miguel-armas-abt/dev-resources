# ARQUITECTURAS DE APLICACIONES JAVA

## Servidor de aplicaciones tradicional
- En esta arquitectura, una JVM se instala sobre un SO junto con un servidor de aplicaciones (como Tomcat, WebLogic, JBoss, etc) para ejecutar aplicaciones Java.
- La JVM es esencial para la ejecución del servidor de aplicaciones, interpretando y ejecutando su bytecode Java.
- Aunque la JVM no participa en la compilación inicial del bytecode, realiza la `compilación JIT`¹, la `gestión de memoria`² y la `carga dinámica de clases`³ consumiendo recursos adicionales.

![Jakarta EE & Microprofile](./images/traditional-architecture.png)

**Reflexión**: La JVM es crítica pero consume recursos significativos.

> **Diccionario**:
> 1. `Compilación JIT (just-in-time)`: Técnica de compilación donde el bytecode se compila en código máquina en tiempo de ejecución. La JVM realiza esta tarea, lo que mejora el rendimiento a largo plazo pero aumenta el consumo de recursos inicial.
> 2. `Gestión de memoria`: La JVM maneja la asignación y liberación de memoria para objetos, incluyendo la recolección de basura para recuperar memoria de objetos no utilizados.
> 3. `Carga dinámica de clases`: Capacidad de la JVM para cargar clases en tiempo de ejecución según sea necesario, proporcionando flexibilidad y modularidad.

## Aplicaciones contenerizadas en servidores
- Docker Engine necesita estar instalado en el SO para ejecutar contenedores.
- Docker empaqueta las aplicaciones con sus propias dependencias y permite ejecutarlas en cualquier entorno.
- Cada contenedor contiene una JVM, lo cual es innecesario, ya que cada contenedor ya incluye todas las dependencias necesarias para la ejecución.
- Tener una JVM en cada contenedor obliga a realiza tareas redundantes.

![Jakarta EE & Microprofile](./images/containerized-architecture.png)

**Reflexión**: La portabilidad de Docker es beneficiosa, pero la redundancia de múltiples JVMs en contenedores distintos resulta en un uso excesivo de recursos.

##  Aplicaciones contenerizadas en un clúster de Kubernetes
- Kubernetes gestiona un clúster de contenedores, asignando recursos dinámicamente y manejando aplicaciones efímeras.
- La ineficiencia de la JVM se acentúa en este entorno, por lo que se exploran alternativas como GraalVM.
- Kubernetes reinicia y redistribuye pods rápidamente, pero cada contenedor aún utiliza una JVM.

![Jakarta EE & Microprofile](./images/containerized-arch+k8s.png)

**Reflexión**: 
- Aunque Kubernetes optimiza la gestión de recursos, la ineficiencia de múltiples JVMs persiste. 
- GraalVM, con su compilación `AOT`¹, puede mejorar la eficiencia al reducir el tiempo de arranque, el uso de memoria y también puede eliminar la necesidad de carga dinámica de clases al compilar todo antes de la ejecución.

> **Diccionario**:
> - `Compilación AOT (ahead-of-time )`: Técnica de compilación donde el bytecode se compila en código máquina antes de la ejecución, eliminando la necesidad de compilación JIT y reduciendo el tiempo de arranque y el uso de memoria.