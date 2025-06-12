# Recursividad

---

La recursividad surge como una respuesta natural a problemas fundamentales en matemáticas y computación. Su origen en la programación se encuentra estrechamente vinculado a varios factores históricos y conceptuales:

- **Raíces matemáticas**: La recursividad tiene sus orígenes en la matemática, donde muchas definiciones y funciones se expresan naturalmente en términos de sí mismas. Por ejemplo, la función factorial, las series de Fibonacci o el algoritmo de Euclides ya se definían recursivamente mucho antes de la existencia de las computadoras.
- **Desarrollo del cálculo lambda**: Con el trabajo de Alonzo Church en los años 1930, el cálculo lambda formalizó la idea de funciones recursivas, estableciendo las bases teóricas para los lenguajes funcionales y la recursividad en programación.
- **Aparición de LISP**: En 1958, John McCarthy desarrolló LISP, uno de los primeros lenguajes de programación que incorporó la recursividad como mecanismo fundamental. LISP fue diseñado para procesar listas (su nombre deriva de "LISt Processing"), estructuras que se manejan naturalmente de forma recursiva.
- **Limitaciones de la iteración**: Se observó que ciertos problemas resultaban extremadamente complejos de resolver mediante enfoques iterativos tradicionales, especialmente aquellos relacionados con estructuras de datos jerárquicas o problemas que requieren backtracking.
- **Adecuación natural a ciertos dominios**: La recursividad emerge como solución idónea para trabajar con estructuras inherentemente recursivas: árboles (como expresiones algebraicas, estructuras sintácticas, jerarquías), recorridos en grafos, y problemas que siguen el patrón "dividir y conquistar".
- **Abstracción y modularidad**: La recursividad permite expresar soluciones a nivel conceptual más alto, más cercano a la definición matemática de los problemas, facilitando el razonamiento sobre algoritmos complejos.

A pesar de su reputación intimidante, la recursividad se basa en dos conceptos sencillos: llamadas a funciones y estructuras de datos de pila. La dificultad no reside en la complejidad del concepto, sino en la forma en que interactúa con mecanismos "invisibles" para el programador, como la pila de llamadas que se gestiona automáticamente durante la ejecución.

---

## Ascenso vs Descenso en Recursión

### ¿Qué es la recursión en descenso?

* Se ejecuta el **trabajo principal antes** de hacer la llamada recursiva.
* Comienza por los casos más grandes y se va acercando al caso base.
* Ejemplo clásico: imprimir los elementos de un array desde el primero hasta el último.

```java
void printForward(int[] arr, int index) {
    if (index >= arr.length) return;
    System.out.println(arr[index]); // Acción antes
    printForward(arr, index + 1);
}
```

---

### ¿Qué es la recursión en ascenso?

* Se ejecuta el **trabajo principal después** de la llamada recursiva.
* Primero llega al caso base, y luego va resolviendo de regreso.
* Ejemplo clásico: invertir una cadena o calcular la suma total de un array.

```java
void printBackward(int[] arr, int index) {
    if (index >= arr.length) return;
    printBackward(arr, index + 1);  // Llamada antes
    System.out.println(arr[index]); // Acción después
}
```

---

### ¿Cuáles son las diferencias clave entre recursión en ascenso y en descenso?

| Característica     | Ascenso                              | Descenso                              |
| ------------------ | ------------------------------------ | ------------------------------------- |
| Orden de ejecución | Trabajo después de la recursión      | Trabajo antes de la recursión         |
| Flujo de pila      | Primero profundidad, luego retorno   | Comienza con trabajo, luego sigue     |
| Común en           | Problemas que se resuelven al volver | Problemas secuenciales o acumulativos |
| Ejemplo típico     | Inversión de cadena, suma acumulada  | Imprimir valores en orden             |

---

### ¿Cuándo usar cada una?

* **Ascenso**: cuando se necesita acumular información de regreso (ej. invertir, calcular, concatenar).
* **Descenso**: cuando se necesita hacer algo en el camino hacia el caso base (ej. impresión, validaciones tempranas).

---
