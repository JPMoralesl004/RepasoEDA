# Hashing

---

## Conceptos Básicos de Hashing

### ¿Qué es una función hash y qué características debe tener?

* Es una función que toma una entrada (clave) y la transforma en un índice dentro de un rango fijo, usado para insertar o acceder rápidamente en estructuras como tablas hash. Debe ser:

  * Determinista (siempre da el mismo resultado para la misma entrada).
  * Uniformemente distribuida.
  * Rápida de calcular.
  * Generar pocas colisiones.

### ¿Qué son las colisiones en hashing y cómo se pueden manejar?

* Una colisión ocurre cuando dos claves distintas producen el mismo valor hash y, por tanto, compiten por la misma posición en la tabla. Se pueden manejar mediante:

  * Encadenamiento (listas en cada posición).
  * Direccionamiento abierto (buscar otra celda disponible).

### ¿Qué impacto tiene una mala función hash sobre el rendimiento?

* Una mala función hash puede causar muchas colisiones, lo que degrada el rendimiento de **O(1)** a **O(n)** en el peor caso. También puede provocar agrupamiento de datos (clustering), desperdicio de espacio y caída en la eficiencia de búsqueda.

### ¿Qué estructuras utilizan hashing internamente?

* `HashMap`, `HashSet`, `Hashtable`, `ConcurrentHashMap`, `EnumMap`, `IdentityHashMap`, además de estructuras similares en otros lenguajes (`dict` en Python, `unordered_map` en C++).

---

## Implementaciones y Técnicas de Resolución de Colisiones

### ¿Qué es el encadenamiento (chaining) y cómo se implementa?

* Es una técnica que guarda múltiples elementos en una misma posición de la tabla mediante una lista (u otra estructura) enlazada. Si hay colisión, el nuevo elemento se agrega a esa lista.

### ¿Qué problemas pueden surgir con el direccionamiento abierto?

* Clustering (agrupamiento de elementos), dificultad para encontrar espacios vacíos cuando la tabla está muy llena, necesidad de usar fórmulas cuidadosas para evitar ciclos infinitos. También obliga a mantener un load factor bajo (< 0.75).

### ¿Qué es el double hashing y cuál es su función?

* Es una técnica de direccionamiento abierto donde, al haber una colisión, se calcula un segundo valor hash para determinar el paso de desplazamiento. Esto reduce el clustering en comparación con probing lineal o cuadrático.

---

## Funciones Hash y Propiedades

### ¿Qué significa que una función hash sea determinista?

* Que siempre produce el mismo valor hash para una misma entrada. Es esencial para que las búsquedas y operaciones sobre tablas hash sean consistentes.

### ¿Cómo afecta la distribución de los valores hash al rendimiento?

* Si los valores hash están bien distribuidos, se minimizan las colisiones y se mantiene la eficiencia de **O(1)**. Una mala distribución genera agrupamientos y reduce el rendimiento.

### ¿Qué es una buena dispersión (spread) en hashing?

* Es cuando los valores hash se distribuyen uniformemente a lo largo del espacio disponible, evitando zonas con muchas colisiones y otras vacías.

### ¿Cuál es la relación entre el tamaño de la tabla y el rendimiento?

* El tamaño de la tabla afecta el **load factor**. Si la tabla es demasiado pequeña, aumentan las colisiones; si es muy grande, se desperdicia memoria. Se busca un equilibrio para mantener eficiencia sin exceso de espacio.

### ¿Qué criterios se deben seguir para diseñar una función hash personalizada?

* Debe usar todas las partes significativas del objeto (por ejemplo, campos importantes).
* Debe producir resultados bien distribuidos.
* Evitar patrones simples.
* Cumplir contrato con `equals()` (si dos objetos son iguales, deben tener el mismo hash).
* Ser rápida de calcular.

---

## Complejidad y Rendimiento

### ¿Cuál es la complejidad esperada de inserción, búsqueda y eliminación en una tabla hash?

* Promedio: **O(1)** para inserción, búsqueda y eliminación.
* Peor caso (muchas colisiones): **O(n)**.

### ¿Qué pasa con la complejidad en caso de muchas colisiones?

* La complejidad se degrada a **O(n)**, ya que todos los elementos podrían caer en la misma posición, transformando la búsqueda en lineal.

### ¿Cómo afecta la carga de la tabla hash (load factor) a su rendimiento?

* Un load factor alto (> 0.75) incrementa las colisiones, lo que reduce la eficiencia. Es común redimensionar (rehashing) cuando se supera un umbral de carga.

### ¿Qué es la redimensión (rehashing) y cuándo ocurre?

* Es el proceso de crear una nueva tabla hash más grande y volver a insertar todos los elementos con nuevos valores hash. Suele ocurrir automáticamente cuando se supera cierto load factor.

### ¿En qué escenarios no conviene usar una tabla hash?

* Cuando:

  * Se necesita mantener los datos ordenados.
  * Se requiere búsqueda de rangos.
  * Las claves cambian dinámicamente (inmutabilidad es clave).
  * Hay restricciones de memoria estrictas (overhead de espacio).

---

## HashMap, HashSet y otras estructuras en Java

### ¿Cómo funciona internamente un `HashMap` en Java?

* Usa una tabla interna de buckets donde cada entrada es una lista (o árbol binario balanceado en Java 8+). Se calcula `hashCode()` y luego se usa para encontrar el índice. En caso de colisión, usa encadenamiento.

### ¿Qué pasa si se modifica la clave de un objeto después de insertarlo en un `HashSet`?

* El objeto se vuelve inaccesible: el hash ya no coincide con su posición original y `HashSet` no puede encontrarlo ni eliminarlo correctamente. Es una violación del contrato `hashCode/equals`.

### ¿Cómo afecta el método `hashCode()` y `equals()` al funcionamiento de un `HashMap`?

* Son esenciales: `hashCode()` determina la posición en la tabla; `equals()` resuelve colisiones. Dos claves distintas pueden tener el mismo hash, pero se consideran iguales si `equals()` lo dice.

### ¿Qué diferencia hay entre `HashMap`, `LinkedHashMap` y `TreeMap`?

* `HashMap`: sin orden garantizado, acceso rápido.
* `LinkedHashMap`: mantiene orden de inserción.
* `TreeMap`: mantiene orden natural (o por comparador), con acceso logarítmico.

---
