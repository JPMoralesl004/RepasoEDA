# Algoritmos 

---

## ¿Qué es un algoritmo?

Un **algoritmo** es un conjunto **finito de pasos bien definidos y ordenados** que resuelven un problema o realizan una tarea específica.

En el contexto de estructura de datos y algorítmica, los algoritmos se estudian en conjunto con cómo **se almacenan los datos** y **cómo se accede a ellos eficientemente**.

---

## ¿Por qué es importante estudiar algoritmos?

Porque:

* Todo programa se basa en algoritmos (aunque no lo veas explícitamente).
* Te permite resolver problemas **eficazmente** y con **buen rendimiento**.
* Saber elegir el algoritmo correcto es clave para escribir software rápido, eficiente y escalable.

---

## Clasificación general de algoritmos

### 1. **Por tipo de problema**

* **De búsqueda:** encontrar un elemento (ej. búsqueda binaria).
* **De ordenamiento:** organizar datos (ej. quicksort, mergesort).
* **De recorrido/travesía:** visitar estructuras como árboles o grafos.
* **De optimización:** encontrar la mejor solución entre varias (ej. Dijkstra).
* **De división y conquista:** resuelven el problema dividiéndolo en subproblemas más pequeños.

---

## Elementos clave de un algoritmo

1. **Entrada:** datos de inicio.
2. **Proceso:** conjunto de pasos (lógica).
3. **Salida:** resultado esperado.
4. **Corrección:** debe hacer lo que se espera.
5. **Eficiencia:** medir su rendimiento en tiempo y espacio.

---

## Análisis de algoritmos: Complejidad

### Complejidad Temporal

Mide **cuánto tiempo tarda** el algoritmo según el tamaño de la entrada (`n`).

* Notación Big-O:

  * `O(1)` → tiempo constante
  * `O(n)` → lineal
  * `O(log n)` → logarítmica
  * `O(n²)` → cuadrática

### Complejidad Espacial

Mide **cuánta memoria** usa el algoritmo.

---

## 📚 Ejemplos clásicos de algoritmos

| Nombre               | Tipo                | Big-O promedio          | Para qué sirve                   |
| -------------------- | ------------------- | ----------------------- | -------------------------------- |
| **Búsqueda binaria** | Búsqueda            | `O(log n)`              | Buscar en lista ordenada         |
| **Bubble sort**      | Ordenamiento        | `O(n²)`                 | Muy simple, pero ineficiente     |
| **Merge sort**       | Ordenamiento        | `O(n log n)`            | Ordenamiento eficiente y estable |
| **DFS/BFS**          | Recorrido de grafos | `O(V + E)`              | Buscar caminos o recorrer nodos  |
| **Dijkstra**         | Optimización        | `O(V log V)` con heap   | Camino más corto en grafos       |
| **Quick sort**       | Ordenamiento        | `O(n log n)` (promedio) | Muy rápido, usado en práctica    |

---
