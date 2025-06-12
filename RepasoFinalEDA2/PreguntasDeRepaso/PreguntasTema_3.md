# Recursividad

---

## Preguntas Generales

### 1. ¿Qué es la recursividad y para qué sirve?

* **Recursividad** es una técnica de programación donde una función se llama a sí misma para resolver un problema dividiéndolo en subproblemas más pequeños del mismo tipo.
* Se utiliza cuando:

  * El problema se puede dividir en subproblemas similares.
  * La solución se expresa naturalmente de forma recursiva (como estructuras jerárquicas o problemas matemáticos).
* Ejemplos clásicos: factorial, Fibonacci, recorridos en árboles, torres de Hanoi.

---

### 2. ¿Qué elementos esenciales debe tener una función recursiva?

* **Caso base**: condición que detiene la recursión. Evita el ciclo infinito.
* **Llamada recursiva**: la función se llama a sí misma con una entrada modificada.
* **Progreso hacia el caso base**: cada llamada se acerca al caso base.

```java
int factorial(int n) {
    if (n == 0) return 1; // caso base
    return n * factorial(n - 1); // llamada recursiva
}
```

---

### 3. ¿Qué ventajas ofrece la recursividad frente a la iteración?

* Código más limpio, conciso y fácil de entender para problemas que tienen naturaleza recursiva (por ejemplo, estructuras de árbol, backtracking).
* Permite resolver problemas de forma más natural y expresiva.

---

### 4. ¿Cuáles son los riesgos o desventajas del uso de la recursividad?

* **Uso de memoria adicional**: cada llamada recursiva se apila en la pila de llamadas.
* **StackOverflowError**: si no hay un caso base claro o se hacen demasiadas llamadas sin terminar.
* Menor rendimiento frente a soluciones iterativas en algunos contextos.

---

### 5. ¿En qué casos conviene evitar la recursividad?

* Cuando el problema se puede resolver de forma más eficiente usando bucles.
* Si el número de llamadas puede crecer mucho y causar desbordamiento de pila.
* En sistemas donde el consumo de memoria o el rendimiento es crítico.

---

## ¿Qué es la recursividad?

La recursividad es una técnica de programación donde una función se llama a sí misma para resolver un problema. 

Se utiliza para dividir problemas grandes en subproblemas más pequeños, más fáciles de manejar.

### ¿Para qué sirve?

* Resolver problemas naturalmente jerárquicos o repetitivos.
* Es útil en:
  - Estructuras de datos recursivas (como árboles o grafos)
  - Problemas de combinatoria
  - Algoritmos de búsqueda, recorrido, y generación
 
### ¿Cuáles son las principales ventajas y desventajas del uso de recursividad frente a soluciones iterativas?

**Ventajas:**
- Código más limpio y expresivo para problemas como árboles, backtracking, combinatoria.
- Divide naturalmente el problema en subproblemas.

**Desventajas:**
- Mayor consumo de memoria (por pila de llamadas).
- Riesgo de StackOverflowError.
- No se optimiza la recursión de cola.

### ¿Qué es el caso base y por qué es esencial en una función recursiva?

- El caso base es la condición que detiene la recursión.
- Es esencial para evitar recursión infinita y para retornar un valor conocido con el cual construir la solución final.

*Ejemplo:*

```java

int factorial(int n) {
    if (n == 0) return 1; // caso base
    return n * factorial(n - 1); // paso recursivo
}

```

### ¿Cómo puede afectar la recursividad al rendimiento y uso de memoria de un programa?

- Cada llamada recursiva se guarda en la pila de ejecución, lo que consume más memoria.
- Puede causar desbordamientos de pila si hay muchas llamadas anidadas.
- El rendimiento puede ser peor que una solución iterativa si se recalculan subproblemas (a menos que se use memoización).

### ¿En qué tipos de problemas es más recomendable usar recursión que iteración?

- Cuando el problema tiene estructura recursiva:
  - Estructuras como árboles y grafos
  - Backtracking (sudoku, laberintos)
  - Problemas como combinaciones, permutaciones, división y conquista (merge sort, quicksort)

### ¿Qué condiciones debe cumplir una función para ser considerada recursiva y funcionar correctamente?

- Debe llamarse a sí misma (condición de recursividad).
- Debe tener un caso base definido, que detenga la recursión.
- Debe acercarse al caso base en cada llamada para evitar ciclos infinitos.

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

## Ascenso vs Descenso en Recursión

---

### ¿Cuál es la diferencia fundamental entre recursión en ascenso y recursión en descenso?

* **Recursión en descenso:** realiza el trabajo antes de la llamada recursiva.
→ Se ejecuta desde el caso más general hacia el base.
* **Recursión en ascenso:** realiza el trabajo después de la llamada recursiva.
→ El flujo baja hasta el caso base y luego sube resolviendo.
* En términos de pila, el descenso "baja haciendo cosas", el ascenso "sube resolviendo".

---

### ¿En qué tipo de problemas es más útil usar recursión en ascenso en lugar de en descenso?

* En problemas donde el resultado final **depende del retorno** de las llamadas recursivas.
* Ejemplos:

  * Invertir una cadena.
  * Calcular una suma total.
  * Construir estructuras desde el final (como un árbol binario desde las hojas hacia la raíz).

---

### ¿Cómo afecta el orden de ejecución (antes o después de la llamada recursiva) al comportamiento del algoritmo?

* **En descenso**, los efectos se ven inmediatamente mientras baja la pila (útil para tareas como imprimir en orden).
* **En ascenso**, los efectos se acumulan y se ejecutan al regresar por la pila (útil para acumulaciones o inversiones).
* El orden cambia la lógica y el flujo del resultado, incluso si la estructura general parece similar.

---

### Da un ejemplo práctico donde la recursión en descenso sea preferida y otro donde la de ascenso sea obligatoria.

* **Descenso preferido**:

  * Imprimir elementos de un array del primero al último.
  * Validar una condición en cada paso antes de seguir (como cortar una búsqueda).

* **Ascenso obligatorio**:

  * Construir una cadena invertida.
  * Evaluar una expresión que depende de los resultados previos (como una suma acumulativa).

---
