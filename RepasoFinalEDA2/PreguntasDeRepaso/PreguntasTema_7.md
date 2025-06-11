# Busqueda

---

## Conceptos Básicos de Búsqueda

### ¿Cuál es la diferencia entre búsqueda exacta y búsqueda aproximada?

* La búsqueda exacta busca coincidencias que se ajusten completamente al valor objetivo. La búsqueda aproximada permite cierto margen de error o diferencia, útil por ejemplo en algoritmos de búsqueda difusa, procesamiento de texto o machine learning.

### ¿Cómo influye la estructura de los datos (ordenados o desordenados) en el tipo de búsqueda que se debe utilizar?

* Si los datos están ordenados, se puede usar **búsqueda binaria**, que es más eficiente. Si no están ordenados, la única opción general es una **búsqueda lineal** o utilizar estructuras adicionales como **hash maps** o **árboles** para optimizar.

### ¿Qué es un criterio de búsqueda y cómo puede definirse en estructuras complejas?

* Un criterio de búsqueda es una condición que define cuándo un elemento es considerado un "match". En estructuras complejas (como objetos), puede definirse mediante funciones lambda, comparadores personalizados o sobrecarga de métodos `equals()`.

### ¿Qué ventajas ofrece la búsqueda en estructuras indexadas?

* Las estructuras indexadas permiten acceder rápidamente a los datos sin recorrer toda la colección. Por ejemplo, un `HashMap` o un `TreeMap` pueden realizar búsquedas en tiempo constante o logarítmico, respectivamente.

### ¿Qué factores determinan la eficiencia de un algoritmo de búsqueda?

* El tamaño de los datos, si están ordenados, el tipo de estructura usada, la complejidad de la comparación, y la frecuencia con la que se repite la búsqueda. También influye si los datos son estáticos o dinámicos.

---

## Funciones y Operaciones de Búsqueda

### ¿Qué función debe implementarse para realizar una búsqueda genérica en una colección?

* Se suele implementar una función que recorra la colección y use un **predicado** (por ejemplo, una función lambda) para determinar si un elemento cumple con el criterio de búsqueda. En Java, podría usarse `stream().filter().findFirst()`.

### ¿Cómo se puede optimizar una búsqueda cuando se repite muchas veces con el mismo patrón?

* Se puede crear una **estructura de índice** (como un `HashMap`, `Trie`, o `TreeMap`) para reducir el tiempo de búsqueda. Otra estrategia es **almacenar en caché** los resultados anteriores si los datos no cambian frecuentemente.

### ¿Cómo afecta la complejidad de comparación (por ejemplo, con objetos) al rendimiento de una búsqueda?

* Si la comparación es costosa (por ejemplo, comparar múltiples campos de un objeto), puede ralentizar significativamente la búsqueda. En esos casos conviene preprocesar, usar índices o reducir el número de comparaciones mediante heurísticas.

### ¿Qué tipo de búsquedas se benefician de usar funciones hash?

* Las búsquedas donde se desea encontrar elementos por claves únicas (como ID, nombre, etc.) se benefician enormemente de estructuras como `HashMap` o `HashSet`, que permiten acceso en tiempo **O(1)** promedio.

---

## Implementaciones de Algoritmos de Búsqueda

### ¿Cómo implementarías una búsqueda sin conocer el tipo exacto de colección?

* Se usaría una interfaz genérica (`Collection<T>`) y se aplicaría una búsqueda lineal con un predicado. Ejemplo:

  ```java
  public <T> T buscar(Collection<T> coleccion, Predicate<T> criterio) {
      for (T item : coleccion) {
          if (criterio.test(item)) return item;
      }
      return null;
  }
  ```

### ¿Qué estructuras de datos son más adecuadas para búsquedas rápidas?

* `HashMap` y `HashSet` para búsquedas por clave en tiempo constante promedio. `TreeMap` o `TreeSet` si se necesita orden. También los **trie** para búsquedas por prefijo y los **índices inversos** para texto.

### ¿Qué técnicas se pueden usar para evitar búsquedas lineales en listas grandes?

* Indexación previa (por hash o árbol), ordenamiento para permitir búsqueda binaria, precálculo de resultados frecuentes (memoización), estructuras como `Map`, y en casos avanzados, uso de bases de datos embebidas.

### ¿Cómo manejarías la búsqueda de elementos duplicados en estructuras no ordenadas?

* Se puede usar un `Map<T, List<T>>` o `Map<T, Integer>` para agrupar o contar ocurrencias mientras se recorre la colección una sola vez. También se puede recolectar múltiples resultados con `stream().filter().collect()`.

---

## Búsqueda Binaria

### ¿Cuál es el requisito fundamental para que una búsqueda binaria funcione?

* Los datos deben estar **ordenados** de antemano. Sin esta condición, los resultados serán incorrectos o inconsistentes.

### ¿Qué errores comunes se cometen al implementar la búsqueda binaria?

* Cálculo incorrecto del índice medio (`(low + high) / 2` puede causar desbordamiento), no ajustar correctamente los límites del rango, o no considerar casos con múltiples ocurrencias del elemento buscado.

### ¿Cómo adaptarías la búsqueda binaria para encontrar el primer o último valor igual?

* Se puede modificar la búsqueda binaria para seguir buscando a la izquierda o derecha incluso después de encontrar el valor, hasta localizar el primer o último índice. Esto se conoce como **lower bound** y **upper bound**.

### ¿Puede aplicarse la búsqueda binaria en estructuras dinámicas como listas enlazadas?

* No directamente. La búsqueda binaria requiere acceso aleatorio a los índices, algo que las listas enlazadas no proporcionan eficientemente. En ese caso, es mejor usar estructuras como árboles balanceados.

---

## Búsqueda Lineal

### ¿Cuál es la principal ventaja de la búsqueda lineal respecto a la binaria?

* No requiere que los datos estén ordenados y funciona sobre cualquier tipo de colección. Es simple de implementar y útil para colecciones pequeñas o únicas.

### ¿En qué casos es más eficiente usar una búsqueda lineal?

* Cuando la colección es pequeña, no se necesita orden, o el coste de ordenar sería mayor que hacer una búsqueda secuencial. También cuando los datos cambian frecuentemente.

### ¿Cómo afecta el tamaño del dataset a la eficiencia de la búsqueda lineal?

* De forma directa: la complejidad es **O(n)**, por lo que a mayor tamaño, mayor tiempo de búsqueda. No escala bien con grandes volúmenes de datos.

### ¿Qué impacto tiene el orden de los datos sobre la búsqueda lineal?

* Si el elemento buscado está al principio, la búsqueda es muy rápida. Si está al final o no está, se recorre toda la colección. El orden no mejora el rendimiento promedio, pero puede afectar casos específicos.

---

## Búsqueda en Árbol

### ¿Qué estructuras de árbol permiten realizar búsquedas eficientes?

* Los árboles de búsqueda binaria (BST), árboles AVL, árboles rojo-negro y árboles B/B+ (en bases de datos). Todos mantienen un orden y permiten búsquedas logarítmicas en promedio.

### ¿Cuál es la diferencia entre búsqueda en un BST y en un árbol balanceado como AVL?

* Un BST puede degradarse a una lista si se inserta en orden. Un AVL siempre se rebalancea, garantizando profundidad logarítmica y mejor rendimiento de búsqueda en el peor caso.

### ¿Qué pasa si se realiza una búsqueda en un árbol desbalanceado?

* El tiempo de búsqueda puede pasar de **O(log n)** a **O(n)** si el árbol se convierte en una lista degenerada (por ejemplo, al insertar datos ya ordenados sin reequilibrar).

### ¿Cómo afecta el recorrido (preorden, inorden, postorden) a los resultados de la búsqueda?

* Los recorridos son útiles para listar o recorrer árboles, no para buscar directamente. Para búsquedas eficientes, se navega comparando en cada nodo, no con un recorrido completo. Sin embargo, un recorrido inorden de un BST da los elementos en orden.

---
