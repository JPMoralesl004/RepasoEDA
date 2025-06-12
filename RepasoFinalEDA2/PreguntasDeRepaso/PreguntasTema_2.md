# Algoritmos

---

## Preguntas Generales

### 1. ¿Qué es un algoritmo y cuáles son sus características esenciales?

* Un **algoritmo** es un conjunto finito y ordenado de instrucciones que resuelven un problema específico o realizan una tarea.
* Características:

  * **Finito**: termina después de un número limitado de pasos.
  * **Definido**: cada paso es claro y no ambiguo.
  * **Entradas**: cero o más.
  * **Salidas**: al menos una.
  * **Efectivo**: cada paso se puede ejecutar en tiempo finito con recursos razonables.

---

### 2. ¿Qué diferencia hay entre un algoritmo y un programa?

* Un **algoritmo** es una idea abstracta (el "cómo" resolver un problema).
* Un **programa** es la implementación concreta de un algoritmo en un lenguaje de programación específico.
* Ejemplo: Un algoritmo de ordenamiento puede expresarse como QuickSort, y el programa sería su implementación en Java, Python, etc.

---

### 3. ¿Qué es la complejidad algorítmica y qué tipos existen?

* La **complejidad algorítmica** mide el uso de recursos (tiempo y/o espacio) en función del tamaño de la entrada.
* Tipos:

  * **Complejidad temporal**: cuánto tarda en ejecutarse.
  * **Complejidad espacial**: cuánta memoria consume.
* Se expresa comúnmente con notación Big-O: O(1), O(n), O(log n), O(n²), etc.

---

### 4. ¿Cómo se evalúa la eficiencia de un algoritmo?

* Mediante:

  * **Análisis de casos**: peor caso, mejor caso, caso promedio.
  * **Big-O** (notación asintótica).
  * **Benchmarking**: pruebas prácticas de tiempo y memoria en distintos inputs.
  * Comparando con otros algoritmos que resuelven el mismo problema.

---

### 5. ¿Cuál es la importancia de la recursividad e iteración en los algoritmos?

* Ambas son formas de repetir operaciones:

  * **Recursividad**: el algoritmo se llama a sí mismo. Ideal para problemas que se resuelven naturalmente dividiéndose en subproblemas (ej. árboles, torres de Hanoi).
  * **Iteración**: usa estructuras como bucles (`for`, `while`). Es más eficiente en consumo de memoria que la recursión en muchos casos.
* La elección depende del problema, la claridad del código y la eficiencia.

---

## sumArray

### ¿Cómo funciona el algoritmo `sumArray` para sumar todos los elementos de un arreglo?

* El algoritmo recorre cada elemento del arreglo y va acumulando su valor en una variable sumatoria.
* Su objetivo es devolver la suma total de todos los elementos del arreglo.

### ¿Cómo se implementa `sumArray` de forma iterativa?

```java
public int sumArray(int[] arr) {
    int sum = 0;
    for (int num : arr) {
        sum += num;
    }
    return sum;
}
```

### ¿Cómo se implementa `sumArray` de forma recursiva?

```java
public int sumArrayRecursive(int[] arr, int index) {
    if (index == arr.length) return 0;
    return arr[index] + sumArrayRecursive(arr, index + 1);
}
```

---

## Búsqueda Binaria

### ¿Qué condición debe cumplirse para poder aplicar la búsqueda binaria?

* El arreglo debe estar **previamente ordenado** en orden ascendente o descendente, dependiendo de la implementación.
* Sin este requisito, la búsqueda binaria no funciona correctamente.

### ¿Cómo se diferencia la implementación iterativa de la recursiva en búsqueda binaria?

* **Iterativa**: Utiliza un bucle `while` con índices `low` y `high`, y evita el uso de pila de llamadas.
* **Recursiva**: Llama a sí misma dividiendo el rango en cada llamada. Puede consumir más memoria si el arreglo es muy grande.

Ejemplo iterativo:

```java
public int binarySearch(int[] arr, int target) {
    int low = 0, high = arr.length - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

### ¿Qué pasa si se aplica búsqueda binaria en un arreglo desordenado?

* La búsqueda binaria puede devolver resultados incorrectos o no encontrar el valor, incluso si está presente.
* **Error lógico común:** asumir que siempre se puede usar búsqueda binaria sin verificar el orden.

---

## findMax

### ¿Cuál es el propósito del algoritmo `findMax`?

* Encontrar y devolver el **valor máximo** dentro de un arreglo de enteros.

### ¿Cómo se puede implementar `findMax` de forma iterativa?

```java
public int findMax(int[] arr) {
    int max = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] > max) max = arr[i];
    }
    return max;
}
```

### ¿Cómo se puede implementar `findMax` de forma recursiva?

```java
public int findMaxRecursive(int[] arr, int index) {
    if (index == arr.length - 1) return arr[index];
    int maxRest = findMaxRecursive(arr, index + 1);
    return Math.max(arr[index], maxRest);
}
```

### ¿Cómo afecta el tamaño del arreglo al rendimiento de `findMax`?

* El rendimiento crece linealmente con el tamaño del arreglo: **O(n)**.
* En arreglos más grandes, el tiempo de ejecución aumenta proporcionalmente.

---

## Big O

### ¿Qué representa la notación Big O en el análisis de algoritmos?

* Describe cómo **crece el tiempo o espacio requerido** por un algoritmo en función del tamaño de entrada `n`.
* Se usa para comparar la eficiencia de algoritmos independientemente del hardware o implementación.

### ¿Qué significan el peor caso, el mejor caso y el caso promedio en el análisis de algoritmos?

* **Mejor caso (Best Case):** el escenario más favorable para el algoritmo.
* **Peor caso (Worst Case):** el escenario más costoso en tiempo o espacio.
* **Caso promedio (Average Case):** el rendimiento esperado considerando una distribución uniforme de entradas.

### ¿Por qué se ignoran las constantes y términos menos significativos en Big O?

* Big O busca describir el comportamiento de crecimiento, no los detalles exactos.
* Por eso, `O(3n + 5)` se simplifica a `O(n)` porque las constantes no afectan la tendencia de escalabilidad.

### ¿Cómo compararías el rendimiento de un algoritmo con complejidad O(n) con uno de O(log n)?

* `O(log n)` crece mucho más lentamente que `O(n)`, por lo que es **más eficiente en escalabilidad**.
* Por ejemplo, para `n = 1,000,000`, `O(log n)` realiza \~20 pasos, mientras que `O(n)` realiza 1,000,000 pasos.

---
