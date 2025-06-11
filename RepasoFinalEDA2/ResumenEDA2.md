# Repaso Examen Final
---

### 📦 **Estructuras de datos ya implementadas en Java**

Java proporciona muchas estructuras listas para usar en el paquete `java.util`:

* **Listas** (`ArrayList`, `LinkedList`) – Listas ordenadas de elementos.
* **Conjuntos (Sets)** (`HashSet`, `LinkedHashSet`, `TreeSet`) – No permiten duplicados.
* **Mapas (Maps)** (`HashMap`, `TreeMap`, `LinkedHashMap`) – Pares clave-valor.
* **Pilas y Colas** (`Stack`, `Queue`, `Deque`) – Estructuras para orden LIFO o FIFO.
* **Arrays** – Estructura básica para manejar elementos indexados.

Estas estructuras están optimizadas con algoritmos eficientes y pueden tener diferentes características en cuanto a orden, acceso y rendimiento.

---

### 🧠 **Big O y Complejidad**

**Big O (O-grande)** describe cómo crece el tiempo o el espacio necesario para ejecutar un algoritmo en función del tamaño de entrada.

Ejemplos comunes:

* `O(1)` – Tiempo constante.
* `O(n)` – Lineal.
* `O(log n)` – Logarítmico (como búsqueda binaria).
* `O(n^2)` – Cuadrático (como algunos algoritmos de ordenación).

La **complejidad** se puede medir en:

* **Tiempo**: Cuánto tarda un algoritmo en ejecutarse.
* **Espacio**: Cuánta memoria utiliza.

---

### 🔁 **Iteración y Recursividad**

Dos formas de recorrer estructuras o resolver problemas:

* **Iteración**: Uso de bucles (`for`, `while`).
* **Recursividad**: Una función que se llama a sí misma.

Ejemplo: recorrer un árbol se puede hacer tanto iterativamente como recursivamente.

---

### 🔍 **Búsqueda**

Consiste en encontrar un elemento dentro de una estructura:

* En **conjuntos ordenados**: se puede usar **búsqueda binaria** (`O(log n)`).
* En **conjuntos desordenados**: se usa **búsqueda lineal** (`O(n)`), porque no hay orden que se pueda aprovechar.

#### ¿Cómo buscarías en un conjunto desordenado?

* Usando **búsqueda lineal**: recorriendo todos los elementos uno a uno.
* Usando una **estructura como `HashSet` o `HashMap`**: búsquedas en `O(1)` promedio gracias a la función hash.

#### ¿Cuántas formas hay de buscar en conjuntos desordenados?

* **Lineal**
* **Por hash**
* **Filtrado con streams** (`stream().filter(...)`)
* **Paralela** con `parallelStream()`

---

### 📊 **Ordenación (Sorting)**

Es reorganizar los elementos en un cierto orden (ascendente, descendente, por nombre, etc.)

* Algoritmos comunes: `Bubble Sort`, `Merge Sort`, `Quick Sort`, etc.
* Java ofrece: `Collections.sort()`, `Arrays.sort()`, y en streams: `.sorted()`.

#### ¿Qué problemas puede haber al ordenar elementos?

* **Múltiples criterios**: por ejemplo, ordenar personas por edad y luego por nombre.
* **Elementos no comparables**: si no implementan `Comparable` o no se proporciona un `Comparator`.
* **Orden estable vs inestable**: si se conserva el orden original de elementos iguales.
* **Inmutabilidad**: si no puedes modificar los objetos directamente.

---

### 🧊 **Inmutabilidad**

Un objeto **inmutable** no puede cambiar después de su creación. Ejemplo clásico en Java: `String`.

Ventajas:

* Seguridad en entornos concurrentes.
* Menor posibilidad de errores.

Desventajas:

* Puede requerir crear muchos objetos nuevos en vez de modificar los existentes.
* Puede ser menos eficiente si se necesita mucha mutabilidad.

---

## Preguntas Examen

- define los criterios para que en un caso de recursividad no se llegue a desborbamiento de la pila

**Respuesta:** 

### ✅ **Criterios clave**

1. **Caso base definido**

   * La función debe tener una condición clara para detenerse.

2. **Avance hacia el caso base**

   * Los parámetros deben cambiar en cada llamada para acercarse al fin.

3. **Validar entradas**

   * Asegura que los datos sean correctos para evitar bucles infinitos.

4. **Recursión de cola (si posible)**

   * Optimiza llamadas si el lenguaje lo permite (Java no lo hace por defecto).

5. **Usar iteración si la recursión es profunda**

   * A veces un `for` o `while` es más seguro y eficiente.

### 🔎 ¿Cómo saber si hay riesgo de `StackOverflowError`?

* Llamadas recursivas sobre datos grandes sin un buen caso base.
* Procesar listas muy largas (como árboles o grafos muy profundos).
* Falta de validación en entradas del usuario.

---
