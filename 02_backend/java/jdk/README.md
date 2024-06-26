# JAVA DEVELOPMENT KIT (JDK)

La JDK es un conjunto de herramientas que proporciona todo lo necesario para desarrollar y ejecutar aplicaciones Java.
Incluye 
- Compilador `javac`
- Java Virtual Machine (JVM)
- Herramientas de desarrollo

## JAVAC
En tiempo de compilación, el compilador `javac` convierte el código fuente escrito en Java (`.java`) en bytecode (`.class`).

## JVM
La JVM principalmente se encarga del `thread scheduling`, el `garbage collection`¹ y la interpretación del bytecode en tiempo de ejecución.
Durante la ejecución de la JVM interactúan los siguientes componentes.

> **Class Loader**: Carga el bytecode en la memoria para ser utilizado durante la ejecución del programa.

> **Interpreter**: El interpreter puede trabajar de dos maneras:
>   - Traduce cada instrucción de bytecode a código de máquina una a una y las ejecuta. Este proceso es lento, pero permite dar inicio a la ejecución del programa sin necesidad de pasar previamente por el `JIT`² compiler.
>   - Una vez que el código nativo es almacenado en caché, el interpreter puede ejecutarlo en lugar de interpretar el bytecode nuevamente.

> **Profiler**: Identifica las partes del código que se ejecutan frecuentemente (hotspots).
 
> **Emitter**: Compila a código máquina nativo los hotspots identificados por el profiler.

> **Code cache**: Almacena el código nativo generado por el JIT compiler, permitiendo que las subsecuentes ejecuciones de 
> esas instrucciones de código sean mucho más rápidas.

**Diccionario**:
1. `Garbage collection`: Gestión automática de memoria.
2. `Compilación just-in-time (JIT)`: Técnica de compilación donde el bytecode se compila en código máquina nativo en tiempo de ejecución.

![JDK](./images/jdk.png)

### JVM como plataforma políglota
La JVM permite la ejecución de múltiples lenguajes de programación, siempre y cuando estos lenguajes puedan compilarse a bytecode de Java (`.class`).
Por ejemplo:

```kotlin
// Kotlin code (KotlinGreeter.kt)
class KotlinGreeter {
    fun greet(name: String) {
        println("Hello, $name!")
    }
}
```

```java
// Java code (Main.java)
public class Main {
    public static void main(String[] args) {
        KotlinGreeter greeter = new KotlinGreeter();
        greeter.greet("World");
    }
}
```

En este ejemplo, el código Java en `Main.java` llama a una clase escrita en Kotlin, `KotlinGreeter.kt`. Ambos se compilan a bytecode y se ejecutan en la misma JVM.
