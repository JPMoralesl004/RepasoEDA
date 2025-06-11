---

## Suma de números en un array

### ¿Cómo funciona la recursividad para sumar los números de un array?

* La recursividad divide el problema en subproblemas: sumar el primer elemento y el resto del arreglo.
* Cada llamada suma el elemento actual y delega el resto del trabajo a la siguiente llamada recursiva.

### ¿Cuál es el caso base en la suma recursiva de un array?

* El caso base ocurre cuando se ha llegado al final del arreglo (índice igual a la longitud).
* En ese punto, se retorna 0 para comenzar a propagar la suma hacia atrás.

### ¿Qué pasa si no se define un caso base en la función recursiva?

* Se produce **una recursión infinita** que lleva al **desbordamiento de pila** (`StackOverflowError` en Java).
* Es crítico definir correctamente el caso base para evitar que la función se siga llamando indefinidamente.

### ¿Cómo afecta la profundidad de la pila al sumar recursivamente un array muy grande?

* Cada llamada recursiva ocupa un marco en la pila de llamadas.
* Si el array es muy grande, se pueden exceder los límites del stack, generando un error.
* En esos casos, es mejor usar la versión iterativa o aplicar recursión de cola (tail recursion) si el lenguaje lo permite.

---

## Inversión de cadenas de texto

### ¿Cuál es el caso base para la recursión en la inversión de cadenas?

* Cuando la longitud de la cadena es 0 o 1, ya está invertida.
* Se retorna la cadena tal cual en ese punto.

### ¿Cómo se construye la cadena invertida en cada llamada recursiva?

* En cada paso, se toma el último carácter y se lo coloca al principio del resultado que retorna la llamada recursiva sobre el resto de la cadena.
* Ejemplo: invertir("hola") → "a" + invertir("hol") → ...

### ¿Qué problemas puede presentar esta recursión en cadenas muy largas?

* Consume mucha memoria por el número de llamadas recursivas anidadas.
* Puede provocar desbordamiento de pila si la cadena es muy extensa.

### ¿Qué diferencias existen entre invertir una cadena con recursión y con un bucle?

* La versión recursiva es más elegante, pero menos eficiente en espacio.
* La versión iterativa es más directa y eficiente en memoria.
* La iterativa se suele preferir en aplicaciones donde el rendimiento es crítico.

---

## Detección de palíndromos

### ¿Cómo se puede usar recursión para detectar si una cadena es un palíndromo?

* Se comparan el primer y el último carácter.
* Si son iguales, se llama recursivamente con la subcadena interna.
* Si no son iguales, se retorna `false`.

### ¿Cuál es el caso base en la detección recursiva de palíndromos?

* Si la longitud de la subcadena es 0 o 1, se considera un palíndromo.
* También si las comparaciones ya han recorrido todos los caracteres.

### ¿Cómo se manejan las comparaciones en cada llamada recursiva?

* Se verifica si `str.charAt(inicio) == str.charAt(fin)`.
* Si es cierto, se hace una llamada con `inicio+1` y `fin-1`.

### ¿Cómo se optimiza la función recursiva para evitar comparaciones redundantes?

* Evitando copiar la cadena o crear nuevas subcadenas.
* Se trabaja con índices de inicio y fin directamente.

---

## Torre de Hanoi

### ¿Cuál es el principio recursivo para resolver la Torre de Hanoi?

* Mover `n-1` discos al auxiliar, mover el disco más grande al destino, luego mover los `n-1` discos del auxiliar al destino.
* Se resuelve el problema dividiéndolo en 3 pasos recursivos.

### 2. ¿Cuál es el caso base en la solución recursiva de la Torre de Hanoi?

* Cuando `n == 1`, se mueve el disco directamente del origen al destino.

---

## Algoritmo Flood Fill

### ¿Cómo se utiliza la recursión en el algoritmo flood fill?

* Se pinta el píxel actual y se hace una llamada recursiva en las 4 (o 8) direcciones vecinas si cumplen el color objetivo.

### ¿Cuál es el caso base para detener la recursión en flood fill?

* Cuando el píxel está fuera de los límites o ya fue procesado o no coincide con el color objetivo.

### ¿Cómo se evita que el algoritmo visite una posición ya procesada?

* Se puede usar una matriz de visitados o cambiar el color del píxel procesado inmediatamente.

### ¿Qué problemas pueden surgir en la implementación recursiva del flood fill?

* Desbordamiento de pila si la región a pintar es muy grande.
* Puede procesar el mismo punto varias veces si no hay control adecuado.

---

## Backtracking

### ¿Qué es backtracking y cómo usa la recursión para explorar soluciones?

* Es una técnica que prueba opciones posibles recursivamente y retrocede cuando una opción no lleva a una solución válida.

### ¿Cuál es el caso base en un algoritmo de backtracking?

* Cuando se ha encontrado una solución completa o se ha llegado a un punto en el que ya no se puede avanzar.

### ¿Cuál es la diferencia entre backtracking y búsqueda exhaustiva?

* Backtracking **descarta caminos inválidos anticipadamente**, reduciendo el espacio de búsqueda.
* La búsqueda exhaustiva revisa todas las combinaciones posibles, incluso las que no tienen sentido.

---

## Recursividad vs Iteración

### ¿Cuáles son las ventajas de usar recursión sobre iteración?

* Código más conciso, elegante y expresivo para problemas como árboles, recorridos, fractales, etc.

### ¿Cuándo es más eficiente usar iteración que recursión?

* Cuando se trabaja con grandes volúmenes de datos o estructuras lineales como arrays.
* Iteración evita desbordamientos de pila y suele usar menos memoria.

### ¿Cómo afecta la recursión a la memoria respecto a la iteración?

* Cada llamada recursiva ocupa espacio en la pila.
* La iteración usa variables locales y no necesita stack adicional.

### ¿Define los criterios para que en un caso de recursividad no se llegue a desbordamiento de la pila?

* Establecer correctamente el caso base.
* Limitar la profundidad de llamadas.
* Usar tail recursion si el lenguaje lo optimiza.
* Considerar reescribir el algoritmo de forma iterativa si es muy profundo.

---
