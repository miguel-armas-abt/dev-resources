# NPM
> `npm install` se utiliza para instalar paquetes y dependencias de `Node.js` en un proyecto de Angular. Estos paquetes se
> definen en el archivo `package.json`

### Instalar Angular:
```shell script
npm install -global @angular/cli@6.2.5 
```

### Instalar Server Express:
```shell script
npm install -global express
```

### Instalar Bootstrap, JQuery y PopperJS:
```shell script
npm install bootstrap jquery popper.js
```
Considere que Bootstrap no se configura automáticamente. Para ello, abra el archivo `angular.json` y ubique los campos
`build` y `options`. A continuación, agregue Bootstrap dentro de sus respectivas colecciones `styles` y `scripts`
```javascript
            "styles": [ 
              "src/styles.css", 
              "./node_modules/bootstrap/dist/css/bootstrap.min.css" 
            ], 
            "scripts": [ 
              "./node_modules/jquery/dist/jquery.slim.min.js", 
              "./node_modules/popper.js/dist/umd/popper.min.js", 
              "./node_modules/bootstrap/dist/js/bootstrap.min.js" 
            ] 
```


### Instalar SweetAlert2:
```shell script
npm install --save sweetalert2 
```

### Instalar Angular Material:
```shell script
npm install --save sweetalert2 
```
