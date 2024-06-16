# SPRING BOOT - INYECCIÓN DE DEPENDENCIAS (DI)

[← Regresar Spring Boot](./../README.md) <br>

Spring Boot facilita la [DI](./../../principles/design-patterns/dependency-injection/README.md) mediante su contenedor de Inversión de Control (IoC).

## Declaración de dependencias
Spring Boot utiliza `estereotipos`¹ para definir los `beans`² gestionados por el `contenedor de Spring`³.

| Estereotipos     | Descripción                                                                                                                                      |  
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| `@Bean`          | Define un método que produce un bean para ser gestionado por el contenedor de Spring.                                                            |
| `@Configuration` | Indica que una clase contiene métodos `@Bean` y puede ser procesada por el contenedor de Spring para generar definiciones de beans.              |
| `@Component`     | Marca una clase como un componente genérico y candidato para ser detectado automáticamente y registrado como un bean en el contenedor de Spring. |
| `@Service`       | Especialización de `@Component` que indica que una clase proporciona lógica de negocio.                                                          |
| `@Repository`    | Especialización de `@Component` que indica que una clase accede a la base de datos o a una fuente de datos.                                      |
| `@Controller`    | Especialización de `@Component` que define un controlador de Spring MVC, gestionando peticiones web.                                             |

> **Diccionario**:
> 1. `Estereotipos`: Anotaciones que especifican al contenedor de Spring el rol y propósito de los bean dentro de la aplicación.
> 2. `Beans`: Representan a los objetos que son instanciados, configurados y destruidos por el contenedor de Spring.
> 3. `Contenedor de Spring`: Infraestructura fundamental de Spring que gestiona la creación, configuración y ciclo de vida de los beans.

```java
@Component
public class Properties {
  //...
}

@Configuration
public class RestTemplateConfig {
  
  @Bean
  public RestTemplate restTemplate(Properties properties) {
    return new RestTemplate(properties);
  }
}
```

## Inyección por constructor

```java
@Service
public class CreditCardService {
  private PaymentProcessor paymentProcessor;

  public CreditCardService(PaymentProcessor paymentProcessor) {
    this.paymentProcessor = paymentProcessor;
  }

  public void pay(CreditCard card, double amount) {
    paymentProcessor.process(card, amount);
  }
}
```

## Inyección automática
Spring Boot brinda las siguientes anotaciones para inyectar beans, permitiendo la resolución automática de dependencias.

| Anotación        | Descripción                                                                                                                 |  
|------------------|-----------------------------------------------------------------------------------------------------------------------------|
| `@Autowired`     | Indica que una dependencia debe ser inyectada automáticamente por Spring. Se puede usar en constructores, métodos y campos. |
| `@Qualifier`     | Utilizada junto con `@Autowired` para especificar cuál bean debe ser inyectado cuando hay múltiples candidatos disponibles. |

```java
@Service
public class CreditCardService {
  
  @Autowired
  private PaymentProcessor paymentProcessor;
  
  public void pay(CreditCard card, double amount) {
    paymentProcessor.process(card, amount);
  }
}
```