### Importar HttpClientModule
```javascript
import { HttpClientModule} from '@angular/common/http'; 
```

```javascript
  imports: [
    ...
        HttpClientModule  //REST
], 
```

### CORS EN SPRING BOOT
Agregue la siguiente anotación en cada RestController de SpringBoot
```java
@CrossOrigin({"http://localhost:4200"})	//Angular 
```

Agregue la siguiente configuración en el API Gateway
```yaml
spring:
  cloud:
    gateway:
      globalcors:
        corsConfigurations:
          '[/**]':
            allowedOrigins: 'http://localhost:4200'
            allowedMethods:
              - GET
              - POST
              - PUT
              - DELETE 
```
