# REGEX

> 📌 **Notas**
> - Una expresión regular (regex) es una notación que permite definir un patrón de formación de cadenas.
> - Con ayuda de la regex podemos verificar si una cadena candidata pertenece o no a este patrón.

| Operador           | Descripción                                                                                | 
|--------------------|--------------------------------------------------------------------------------------------|
| `{} () []`         | Operadores de agrupación                                                                   |
| `.`                | Cualquier carácter excepto nueva línea \n                                                  |
| `[abc]`            | Carácter `a`, `b` o `c`                                                                    |
| `[a-z]`            | Desde a hasta z                                                                            |
| `?`                | Cero o uno del elemento precedente                                                         |
| `*`                | Cero o más del elemento precedente                                                         |
| `+`                | Uno o más del elemento precedente                                                          |
| `aa \| bb`         | Cualquiera aa o bb                                                                         |
| `{m,n}`            | Entre m y n del elemento precedente                                                        |
| `\.`               | Escapar un símbolo (por ejemplo \*, \(, \\, etc)                                           |
| `^`                | El inicio de la cadena                                                                     |
| `$`                | El final de la cadena                                                                      |
| `\d, \w, \s`       | Un dígito, carácter `[A-Za-z0-9]`, o espacio                                               |
| `\D, \W, \S`       | Cualquiera excepto un dígito, carácter o espacio                                           |
| `[^abc]`           | Cualquier carácter excepto `a`, `b` o `c`                                                  |
| `{n}`              | Exactamente más del elemento precedente                                                    |
| `{n,}`             | n o más del elemento precedente                                                            |
| `??, *?, +?, {n}?` | Igual que lo anterior, pero tan poco como sea posible                                      |
| `(expr)`           | Captura lo uqe está en paréntesis como un grupo para su posterior uso con `\1`, `\2`, etc. |
| `(?:expr)`         | Agrupa una expresión sin que se capture                                                    |
| `(?=expr)`         | Seguido por la expresión                                                                   |
| `(?!expr)`         | No seguido por la expresión                                                                |