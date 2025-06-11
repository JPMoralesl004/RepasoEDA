# Estructura de datos

## ArrayDeque

### - ¿Cuáles son las ventajas de usar `ArrayDeque` sobre `LinkedList` para implementar colas y pilas?**

* `ArrayDeque` usa un arreglo circular interno, lo que le da un **mejor rendimiento en acceso a memoria** y menor overhead que `LinkedList`, que usa nodos enlazados.
* `ArrayDeque` no tiene sobrecarga de objetos extra (nodos) ni referencias, haciendo que sus operaciones sean más rápidas y eficientes en memoria.
* En general, `ArrayDeque` es **más rápido** para operaciones de inserción y eliminación en ambos extremos (cola y pila).
* `ArrayDeque` no permite elementos nulos, lo que evita problemas inesperados.

### - ¿Cómo se diferencia el rendimiento de `ArrayDeque` en inserciones y eliminaciones en comparación con `LinkedList`?**

* Ambas estructuras tienen operaciones `O(1)` amortizadas para inserciones y eliminaciones en los extremos.
* Sin embargo, `ArrayDeque` suele ser **más eficiente en la práctica** por mejor localización en memoria (menos saltos de punteros).
* `LinkedList` tiene mayor overhead por la necesidad de mantener referencias a nodos anteriores y siguientes.
* Para operaciones no en los extremos, `LinkedList` puede tener ventaja porque no requiere desplazamientos, pero normalmente no se usan esas operaciones.

### - ¿Qué métodos específicos ofrece `ArrayDeque` para manejar tanto colas como pilas?**

* Para manejar **como pila**:

  * `push(E e)` — agrega al tope
  * `pop()` — elimina y devuelve el tope
  * `peek()` — consulta el tope sin eliminar

* Para manejar **como cola**:

  * `addLast(E e)` / `offerLast(E e)` — inserta al final
  * `removeFirst()` / `pollFirst()` — elimina y devuelve el primer elemento
  * `peekFirst()` — consulta el primer elemento sin eliminar

---

## ArrayList

### - ¿Cómo maneja `ArrayList` la expansión automática del arreglo interno?

* Cuando el arreglo interno está lleno, `ArrayList` crea un nuevo arreglo con mayor capacidad (usualmente 1.5 veces el tamaño actual).
* Luego, copia todos los elementos del arreglo antiguo al nuevo.
* Esta expansión es **costosa**, pero ocurre pocas veces, por lo que el costo se amortiza en muchas operaciones.
* Esto permite que el acceso por índice sea rápido, pero las inserciones que desencadenan expansión son más lentas.

### - ¿Cuándo es mejor usar un `ArrayList` en lugar de un `LinkedList`?

* Cuando se requiere **acceso rápido a elementos por índice** (`get(index)`) — `ArrayList` tiene acceso `O(1)` vs `O(n)` en `LinkedList`.
* Cuando las inserciones y eliminaciones son **principalmente al final** o no frecuentes en posiciones intermedias.
* Cuando se busca **mejor rendimiento en uso de memoria** (menos overhead que `LinkedList`).
* Cuando no hay necesidad de iterar muchas veces insertando/eliminando elementos en medio de la lista.

### - ¿Cómo afecta el tamaño inicial del `ArrayList` al rendimiento?

* Un tamaño inicial grande puede reducir o eliminar la necesidad de expansiones durante inserciones, mejorando rendimiento.
* Si el tamaño inicial es muy pequeño, habrá varias expansiones y copias, afectando la eficiencia.
* Si se conoce la cantidad aproximada de elementos, inicializar con capacidad correcta es una buena práctica.

---

## EnumSet

### - ¿Qué es un `EnumSet` y cuándo es más eficiente que otras colecciones?

* `EnumSet` es una implementación especializada de `Set` para tipos `enum`.
* Internamente usa un **bitmap** (bits) para representar la presencia o ausencia de elementos, haciendo las operaciones muy rápidas.
* Es más eficiente que otros `Set` (como `HashSet`) porque no usa hashing ni objetos adicionales.
* Ideal para manejar subconjuntos de constantes enumeradas con operaciones como unión, intersección y diferencia.

### - ¿Por qué `EnumSet` solo funciona con tipos `enum`?

* Porque está diseñado para aprovechar que los valores `enum` son un conjunto fijo y limitado.
* La implementación usa internamente bits, cada bit representa un valor del `enum`.
* No tendría sentido usarlo con tipos no `enum` porque no se puede garantizar un conjunto finito y acotado de valores.

### - ¿Cuáles son las limitaciones de `EnumSet` en comparación con otros `Set`?

* Solo puede usarse con tipos `enum`.
* No soporta elementos nulos (igual que `Enum` no puede tener `null`).
* No es adecuado si se necesita almacenar tipos heterogéneos o valores fuera del conjunto `enum`.
* Su funcionalidad está limitada a operaciones sobre conjuntos de valores constantes.

---

## LinkedList

### - ¿Qué diferencias hay entre `LinkedList` y `ArrayList` en términos de inserción y acceso?

* Acceso:

  * `ArrayList` tiene acceso por índice `O(1)`.
  * `LinkedList` tiene acceso `O(n)` porque debe recorrer nodos.

* Inserción y eliminación:

  * En posiciones arbitrarias, `LinkedList` es más eficiente `O(1)` si ya tienes el nodo.
  * `ArrayList` puede ser costoso porque necesita desplazar elementos `O(n)`.

* Para insertar o eliminar al inicio o final:

  * `LinkedList` es `O(1)` (doblemente enlazada).
  * `ArrayList` es `O(n)` para inicio, `O(1)` amortizado para final.

### - ¿Cómo funciona la implementación doblemente enlazada en `LinkedList`?

* Cada nodo contiene referencias a su nodo anterior y siguiente.
* Esto permite recorrer la lista en ambas direcciones.
* Facilita inserciones y eliminaciones rápidas sin mover otros elementos.
* También facilita eliminar nodos sin tener que recorrer desde el inicio (si tienes el nodo).

### - ¿Qué casos de uso específicos favorecen a `LinkedList`?

* Cuando hay muchas inserciones y eliminaciones en posiciones arbitrarias o en los extremos.
* Cuando no se requiere acceso frecuente por índice.
* Cuando se necesita implementar colas o pilas donde la velocidad en extremos es crítica.
* Cuando se quiere evitar la copia o el reordenamiento de datos en memoria.

---

## PriorityQueue

### - ¿Cómo determina `PriorityQueue` el orden de sus elementos?

* `PriorityQueue` usa un **heap binario** internamente.
* El orden se determina por el **orden natural** de los elementos (implementando `Comparable`) o por un `Comparator` proporcionado.
* El elemento con la prioridad más alta (según criterio) está siempre en la raíz del heap y es el primero en salir.

### - ¿Qué complejidad tiene insertar y eliminar en una `PriorityQueue`?

* La inserción (`offer`) es `O(log n)` porque el heap debe reorganizarse.
* La eliminación del elemento con mayor prioridad (`poll`) también es `O(log n)`.
* La consulta del elemento mínimo o máximo (`peek`) es `O(1)`.

### - ¿Se puede usar `PriorityQueue` para ordenar elementos en orden inverso? ¿Cómo?

* Sí, se puede usar un `Comparator` inverso al construir la `PriorityQueue`.
  Ejemplo:

  ```java
  PriorityQueue<Integer> pq = new PriorityQueue<>(Comparator.reverseOrder());
  ```
* Esto hace que el heap priorice los elementos más grandes primero, logrando un orden inverso.

---

## Stack

### - ¿Cuál es la diferencia entre la clase `Stack` y una pila implementada con `Deque`?

* La clase `Stack` es una **clase antigua (legacy)** que extiende `Vector`, y por tanto es sincronizada (lo que puede afectar rendimiento).
* `Deque` es una interfaz moderna que puede usarse para implementar pilas con mejor rendimiento y sin sincronización innecesaria.
* Se recomienda usar `ArrayDeque` (implementa `Deque`) para pilas en Java actual.
* `Stack` tiene métodos como `push()`, `pop()`, `peek()` que funcionan igual que una pila.

### - ¿Por qué se recomienda usar `Deque` en lugar de la clase `Stack` en Java moderno?

* Porque `Deque` (como `ArrayDeque`) tiene **mejor rendimiento**, es no sincronizado y más flexible.
* `Stack` es menos eficiente debido a la sincronización y herencia de `Vector`.
* `Deque` puede funcionar como pila o cola doble.
* Es la recomendación oficial de Oracle desde Java 6 en adelante.

---

## Vector

### - ¿Cuál es la diferencia principal entre `Vector` y `ArrayList`?

* `Vector` es **sincronizado**, lo que significa que sus métodos son seguros para acceso concurrente, pero esto afecta rendimiento.
* `ArrayList` no es sincronizado, por lo que es más rápido en contextos de un solo hilo.
* Ambos usan un arreglo interno para almacenar datos y tienen acceso `O(1)`.

### - ¿Por qué `Vector` es sincronizado y qué implicaciones tiene para el rendimiento?

* `Vector` sincroniza sus métodos para evitar problemas en entornos multihilo.
* La sincronización añade overhead y puede causar bloqueos innecesarios en contextos no concurrentes.
* Por eso, en aplicaciones modernas, se prefiere usar `ArrayList` y manejar sincronización explícita si es necesario.

### - ¿Cuándo es adecuado usar `Vector` hoy en día?

* Cuando se trabaja en un entorno multihilo muy simple donde no se quiere gestionar sincronización manualmente.
* En código legacy que ya usa `Vector`.
* En general, se prefieren otras alternativas (como `Collections.synchronizedList` o `CopyOnWriteArrayList`) para casos multihilo.

---

# Tabla comparativa de estructuras

| Estructura       | Acceso aleatorio | Inserción/Eliminación inicio | Inserción/Eliminación final | Sincronización | Uso ideal                                                                 |
|------------------|------------------|-------------------------------|------------------------------|----------------|---------------------------------------------------------------------------|
| ArrayList        | O(1)             | O(n)                          | Amortiguado O(1)             | No             | Listas con acceso rápido y pocas inserciones/remociones intermedias      |
| LinkedList       | O(n)             | O(1)                          | O(1)                          | No             | Listas con muchas inserciones/eliminaciones en extremos o intermedios    |
| ArrayDeque       | No soportado     | O(1)                          | O(1)                          | No             | Colas/pilas con operaciones rápidas en ambos extremos                    |
| PriorityQueue    | No soportado     | O(log n)                      | O(log n)                      | No             | Colas de prioridad para ordenamiento parcial rápido                      |
| Stack            | No soportado     | O(1)                          | O(1)                          | Sí (legacy)    | Pilas clásicas, aunque se recomienda `Deque` actualmente                 |
| Vector           | O(1)             | O(n)                          | Amortiguado O(1)             | Sí             | Contextos multihilo simples con sincronización automática                |
| EnumSet          | N/A              | N/A                           | N/A                           | No             | Manejo eficiente de conjuntos de enums con operaciones de conjunto       |
