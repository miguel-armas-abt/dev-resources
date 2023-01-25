# Expresiones regulares
> Una expresión regular (ER) es una notación para cadenas de símbolos que tienen un patrón de formación regular. El lenguaje generado por una ER es L(ER). 

> Las expresiones regulares son importantes porque permiten definir un patrón de formación, el cual nos sirve para formalizar un lenguaje y resolver el problema de la pertenencia, es decir, la ER se puede aplicar a una cadena candidata, y si la cumple entonces es sentencia del lenguaje. En una ER se utilizan las siguientes convenciones: 

> `a+`: Uno o más símbolos a 

> `a*`: Cero o más símbolos a

> `a?`: Cero o un símbolo a 

> `{} () [] `: Operadores de agrupación 

> `|`: Alternancia

 ## Operadores
> `.`: Cualquier carácter excepto nueva línea \n

> `[abc]`: Carácter a, b o c

> `[a-z]`: Desde a hasta z
 
> `?`: Cero o uno del elemento precedente

> `*`: Cero o más del elemento precedente

> `+`: Uno o más del elemento precedente

> `aa | bb`: Cualquiera aa o bb

> `{m,n}`: Entre m y n del elemento precedente
 
> `\.`: Un punto (y así, por ejemplo \*, \(, \\, etc)

> `^`: El inicio de la cadena
  
> `$`: El final de la cadena

> `\d, \w, \s`: Un dígito, carácter [A-Za-z0-9], o espacio

> `\D, \W, \S`: Cualquiera excepto un dígito, carácter o espacio

> `[^abc]`: Cualquier carácter excepto a, b o c

> `{n}`: Exactamente más del elemento precedente

> `{n,}`: n o más del elemento precedente

> `??, *?, +?, {n}?`: Igual que lo anterior, pero tan poco como sea posible

> `(expr)`: Captura expre como grupo para su uso con \1, etc.

> `(?:expr)`: Agrupa símbolos, sin que se capture

> `(?=expr)`: Seguido por expr

> `(?!expr)`: No seguido por expr