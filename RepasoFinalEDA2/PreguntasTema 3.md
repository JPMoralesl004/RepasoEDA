## Suma de números en un array

### ¿Cómo funciona la recursividad para sumar los números de un array?

* Divide el problema en subproblemas: sumar el primer elemento y el resto del arreglo recursivamente.
* Cada llamada se encarga de sumar un elemento y delegar el resto.

### ¿Cuál es el caso base en la suma recursiva de un array?

* El caso base se da cuando se alcanza el final del arreglo (índice igual a la longitud).
* Se retorna 0.

### ¿Qué pasa si no se define un caso base en la función recursiva?

* Se produce **una recursión infinita**, que lleva a un **StackOverflowError**.

### ¿Cómo afecta la profundidad de la pila al sumar recursivamente un array muy grande?

* Aumenta el uso de memoria en la pila de llamadas.
* Puede causar errores si el array es muy largo.

---

## Inversión de cadenas de texto

### ¿Cuál es el caso base para la recursión en la inversión de cadenas?

* Si la cadena tiene 0 o 1 caracteres, ya está invertida.

### ¿Cómo se construye la cadena invertida en cada llamada recursiva?

* Se toma el último carácter y se concatena con la inversión del resto.

### ¿Qué problemas puede presentar esta recursión en cadenas muy largas?

* Puede provocar **desbordamiento de pila** debido a la profundidad de llamadas.

### ¿Qué diferencias existen entre invertir una cadena con recursión y con un bucle?

* Recursiva: más expresiva, menos eficiente.
* Iterativa: más eficiente en memoria y velocidad.

---

## Detección de palíndromos

### ¿Cómo se puede usar recursión para detectar si una cadena es un palíndromo?

* Comparar primer y último carácter, y verificar recursivamente la subcadena interna.

### ¿Cuál es el caso base en la detección recursiva de palíndromos?

* Si la subcadena es de longitud 0 o 1, es un palíndromo.

### ¿Cómo se manejan las comparaciones en cada llamada recursiva?

* Se compara `str.charAt(inicio)` con `str.charAt(fin)`.

### ¿Cómo se optimiza la función recursiva para evitar comparaciones redundantes?

* Usar índices en lugar de crear nuevas subcadenas.

---

## Torre de Hanoi

### ¿Cuál es el principio recursivo para resolver la Torre de Hanoi?

* Mover `n-1` discos al auxiliar, luego el disco grande al destino y finalmente los `n-1` al destino.

### ¿Cuál es el caso base en la solución recursiva de la Torre de Hanoi?

* Cuando `n == 1`, se mueve directamente el disco del origen al destino.

---

## Flood Fill

### ¿Cómo se utiliza la recursión en el algoritmo flood fill?

* Se colorea el píxel actual y se hace flood fill en las 4 (o 8) direcciones.

### ¿Cuál es el caso base para detener la recursión en flood fill?

* Si el píxel ya está fuera de límites, coloreado o no coincide con el color objetivo.

### ¿Cómo se evita que el algoritmo visite una posición ya procesada?

* Usando una matriz de visitados o cambiando el color inmediatamente.

### ¿Qué problemas pueden surgir en la implementación recursiva del flood fill?

* Desbordamiento de pila por una región muy grande.
* Reprocesamiento de píxeles si no se controla bien.

---

## Backtracking

### ¿Qué es backtracking y cómo usa la recursión para explorar soluciones?

* Es una técnica que explora soluciones posibles y retrocede si no llevan a un resultado válido.

### ¿Cuál es el caso base en un algoritmo de backtracking?

* Cuando se ha construido una solución válida o no se puede continuar.

### ¿Cuál es la diferencia entre backtracking y búsqueda exhaustiva?

* **Backtracking** corta ramas que no tienen solución.
* **Búsqueda exhaustiva** prueba todas las combinaciones.

---

## Recursividad vs Iteración

### ¿Cuáles son las ventajas de usar recursión sobre iteración?

* Más legible en problemas como árboles, recorridos o combinaciones.

### ¿Cuándo es más eficiente usar iteración que recursión?

* En estructuras lineales o cuando hay gran volumen de datos.

### ¿Cómo afecta la recursión a la memoria respecto a la iteración?

* Usa pila de llamadas, lo que consume más memoria.

### Define los criterios para que en un caso de recursividad no se llegue a desbordamiento de la pila

* Tener un **caso base bien definido**.
* Evitar llamadas innecesarias.
* Usar **recursión de cola** si es posible.
* Reescribir en forma iterativa si hay riesgo de stack overflow.

---
