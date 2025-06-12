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

## ¿Qué es?

La **recursividad** es una técnica de programación en la que una **función se llama a sí misma** para resolver un problema dividiéndolo en **subproblemas más pequeños** del mismo tipo, hasta llegar a un caso base que se puede resolver directamente.

Esta técnica se basa en dos elementos clave:

1. **Caso base:** condición que detiene la recursión (cuando ya no se llama a sí misma).
2. **Llamada recursiva:** la función se llama a sí misma con un valor más simple o reducido.

La recursividad se fundamenta en el principio matemático de la **inducción** y es una herramienta muy poderosa para resolver problemas que tienen una estructura **repetitiva o jerárquica**.

La recursión puede definirse desde diferentes perspectivas:

<div align=center>

|Definición general|En programación|
|-|-|
|Una cosa recursiva es aquella cuya definición incluye a sí misma.|Una función recursiva es aquella que se llama a sí misma durante su ejecución.|
|Es una definición auto-referencial.|Esta auto-referencia debe tener condiciones específicas para evitar problemas.|

</div>

---

## ¿Para qué se usa?

La recursividad se utiliza para resolver problemas que:

* Se pueden **dividir en subproblemas del mismo tipo**.
* Tienen una **estructura naturalmente recursiva** (como árboles o fractales).
* Son más fáciles de entender o implementar de forma recursiva que iterativa.

### Ejemplos comunes de uso:

* Cálculo de factoriales (`n!`)
* Secuencia de Fibonacci
* Recorrido de estructuras de árbol (preorden, inorden, postorden)
* Algoritmos de búsqueda como DFS (Depth-First Search)
* Problemas de backtracking (sudoku, laberintos, combinaciones)
* Divide y vencerás (mergesort, quicksort)

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

## ¿Cuándo se utiliza?

Usa **recursividad** cuando:

1. ✅ El problema se puede **dividir en subproblemas del mismo tipo** (auto-similar).
2. ✅ Es más fácil o más natural que usar bucles.
3. ✅ Se trabaja con **estructuras jerárquicas** como árboles, grafos o directorios.
4. ✅ Necesitas **explorar todas las posibilidades** (como en backtracking).

### Casos típicos:

* **Árboles:** recorrer nodos (inorden, preorden, postorden).
* **Fractales o estructuras auto-repetitivas.**
* **Algoritmos divide y vencerás:** como `mergesort`, `quicksort`.
* **Problemas de conteo/combinatoria:** torres de Hanoi, caminos posibles, combinaciones.
* **Búsqueda en profundidad (DFS):** en grafos o laberintos.

---

## ¿Cómo se utiliza?

### Definiciones esenciales

Para entender la recursión, es necesario comprender dos conceptos clave:

1. **Caso base**: Es la condición que detiene la recursión. Cuando se cumple, la función no hace más llamadas recursivas y simplemente retorna un valor. Sin un caso base, la recursión nunca terminaría (causando un "stack overflow").

2. **Caso recursivo**: Es la parte donde la función se llama a sí misma, normalmente con argumentos diferentes o avanzando hacia el caso base.

### La pila de llamadas (call stack)

Para comprender completamente cómo funciona la recursión, es fundamental entender el "call stack":

- Cada vez que se llama a una función, se crea un "frame" (marco) que se coloca en la pila.
- Este frame contiene:
  - La dirección de retorno (a dónde volver cuando termine la función)
  - Los argumentos pasados a la función
  - Las variables locales creadas durante la ejecución de la función
- Cuando la función termina, su frame se elimina de la pila y la ejecución vuelve al punto desde donde se llamó.
- Si una función se llama a sí misma repetidamente sin retornar, la pila crece hasta que se produce un "stack overflow" (desbordamiento de pila).

La estructura básica de una función recursiva tiene dos partes **imprescindibles**:

<div align=center>

<table>
<tr>
<td valign=top>

```java
public class Example {
    public static void a() {
        String spam = "Ant";
        System.out.println("spam is " + spam);
        b();
        System.out.println("spam is " + spam);
    }
    
    public static void b() {
        String spam = "Bobcat";
        System.out.println("spam is " + spam);
        c();
        System.out.println("spam is " + spam);
    }
    
    public static void c() {
        String spam = "Coyote";
        System.out.println("spam is " + spam);
    }
    
    public static void main(String[] args) {
        a();
    }
}
```
</td>
<td valign=top>

```
spam is Ant
spam is Bobcat
spam is Coyote
spam is Bobcat
spam is Ant
```
</td>
</tr>
</table>

|![](/images/callStack.webp)
|:-:
|El estado de la pila de llamadas mientras se ejecuta el programa `Example.java`
|![](/images/callStackOverflow.webp)
|Un desbordamiento de pila ocurre cuando la pila de llamadas se vuelve demasiado alta y demasiados objetos *marco* ocupan la memoria.


<table>
<tr>
<td valign=top>

```java
public class Shortest {
    public static void shortest() {
        shortest();
    }
    
    public static void main(String[] args) {
        shortest();
    }
}
```
</td>
<td valign=top>

```
Exception in thread "main" java.lang.StackOverflowError
    at Shortest.shortest(Shortest.java:3)
    at Shortest.shortest(Shortest.java:3)
    at Shortest.shortest(Shortest.java:3)
    at Shortest.shortest(Shortest.java:3)
    at Shortest.shortest(Shortest.java:3)
    ...
    
```
</td>
</tr>
</table>

</div>

### 🚬

```java
public static void cuentaAtrasAdelante(int number) {

    System.out.println(number);

    if (number == 0) {
        System.out.println("Llegamos al caso base.");
        return;
    }
    else {
        cuentaAtrasAdelante(number - 1);
        System.out.println(number + " volviendo");
    }
}
```

<details>

<summary>Detalle de operaciones para cuentaAtrasAdelante(3)</summary>

<div align=center>

|Fase de descenso|Caso base|Fase de ascenso|
|:-:|:-:|:-:|
|3
|2
|1
|0
||Llegamos al caso base.||
|||1 volviendo
|||2 volviendo
|||3 volviendo

</div>

</details>

---

### 1. Caso base (condición de parada):

Evita que la función se llame infinitamente. Define cuándo debe **terminar** la recursión.

### 2. Llamada recursiva:

La función se llama a sí misma con un valor **más simple o reducido**.

---

### Ejemplo 1: Factorial de un número

```java
int factorial(int n) {
    if (n == 0) return 1;         // Caso base
    return n * factorial(n - 1);  // Llamada recursiva
}
```

* Llama a sí misma con `n - 1`.
* Se detiene cuando `n == 0`.

---

### Ejemplo 2: Recorrer un árbol binario (preorden)

```java
void preorden(Nodo nodo) {
    if (nodo == null) return;         // Caso base
    System.out.println(nodo.valor);  // Proceso actual
    preorden(nodo.izquierdo);        // Llamada recursiva
    preorden(nodo.derecho);
}
```

* Recorre primero el nodo actual, luego subárbol izquierdo y derecho.
* Es mucho más intuitivo usar recursividad que bucles en estructuras como árboles.

Para implementar correctamente una función recursiva, deben seguirse estos pasos:

1. **Identificar el caso base**: Se debe definir claramente cuándo la recursión debe detenerse. Esta es la condición más simple del problema que puede resolverse directamente.
1. **Definir el caso recursivo**: Es necesario formular cómo el problema se reduce a una instancia más pequeña de sí mismo.
1. **Garantizar el progreso**: Cada llamada recursiva debe acercarse al caso base, reduciendo el tamaño o la complejidad del problema.
1. **Unificar las soluciones**: Se debe determinar cómo combinar los resultados de las llamadas recursivas para obtener la solución del problema original.

### Consideraciones importantes

- **Verificación del caso base**: Es crucial asegurarse de que todas las llamadas recursivas eventualmente lleguen al caso base.
- **Profundidad de recursión**: Debe tenerse en cuenta la limitación del tamaño de la pila de llamadas en el entorno de ejecución.
- **Eficiencia**: A veces, las soluciones recursivas pueden ser menos eficientes que las iterativas debido a la sobrecarga de las llamadas a funciones.
- **Recursión de cola**: Un tipo especial de recursión donde la llamada recursiva es la última operación en la función, lo que permite optimizaciones en algunos lenguajes.
- **Memorización**: Técnica para almacenar resultados intermedios y evitar cálculos redundantes en funciones recursivas.

---
