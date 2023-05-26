# ANGULAR
> `ng add` se utiliza para agregar nuevas características específicas de Angular a un proyecto existente

### Mostrar versión y ayuda:
```shell script
ng --help 
ng --version
```

### Crear nuevo proyecto:
- `--routing` Agregar routing
```shell script
ng new <project-name>
```

### Crear nuevo componente:
- `--skipTests=true` Omitir test
- `--flat` sin carpeta
```shell script
ng g c <directory-name>/<component-name>
```
Ejemplos:
- `ng g c components/courses --skipTests=true`
- `ng g c components/courses/course-form --flat --skipTests=true`

### Crear nuevo módulo:
```shell script
ng g m <directory-name>/<module-name>
```

### Crear nueva clase:
```shell script
ng g class <directory-name>/<class-name>
```
Ejemplos:
- `ng g class models/course --skipTests=true`

### Crear nueva interface:
```shell script
ng g interface <directory-name>/<interface-name>
```
Ejemplos:
- `ng g interface models/generic-model`

### Crear nuevo service:
```shell script
ng g service <directory-name>/<service-name>
```
Ejemplos:
- `ng g s services/courses --skipTests=true`


### Levantar servidor:
```shell script
ng serve -o
```

### Instalar Angular Material:
```shell script
ng add @angular/material
```
