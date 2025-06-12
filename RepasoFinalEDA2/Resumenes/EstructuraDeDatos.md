# Estructura de Datos

---

## ¿Qué son las estructuras de datos?

Las **estructuras de datos** son formas organizadas de almacenar y gestionar datos en la memoria de un computador para que puedan ser utilizados de manera eficiente.

Sirven para:

* Organizar datos de forma lógica.
* Facilitar el acceso y modificación de esos datos.
* Mejorar el rendimiento de algoritmos.

---

## Clasificación de las estructuras de datos

### 1. **Estructuras de datos primitivas**

Son las más básicas y están directamente soportadas por los lenguajes de programación.

* **Enteros (int)**
* **Reales (float/double)**
* **Caracteres (char)**
* **Booleanos (bool)**

### 2. **Estructuras de datos no primitivas**

Son más complejas y se construyen a partir de las primitivas.

#### a. **Estructuras lineales**

Los elementos se organizan uno tras otro.

* **Arreglos (Arrays):** Colección de elementos del mismo tipo, acceso por índice.
* **Listas enlazadas:** Nodos conectados mediante punteros.
* **Pilas (Stacks):** LIFO (Last In, First Out).
* **Colas (Queues):** FIFO (First In, First Out).

#### b. **Estructuras no lineales**

Organizan los datos jerárquicamente o en redes.

* **Árboles:** Como el árbol binario, AVL, B+.
* **Grafos:** Conjuntos de nodos conectados por aristas.
* **Conjuntos (Sets):** Colección no ordenada y sin elementos repetidos.
* **Tablas hash (Hash tables):** Almacenan datos por clave-valor.

---

## ¿Por qué son importantes?

Las estructuras de datos permiten:

* Reducir la complejidad algorítmica.
* Optimizar el uso de memoria.
* Implementar funciones esenciales como búsqueda, ordenamiento y recorrido.

---

---

## 1. `ArrayList`

### ¿Qué es?

Una lista dinámica basada en un array redimensionable. Internamente usa un array que crece automáticamente cuando se llena.

### ¿Por qué existe?

Porque los arrays normales en Java tienen tamaño fijo. `ArrayList` resuelve eso permitiendo agregar elementos sin preocuparte por el tamaño.

### ¿Para qué sirve?

Ideal cuando necesitas una **lista ordenada** donde:

* Accedes mucho por índice (ej. `get(i)`).
* Agregas casi siempre al final.
* No haces muchas inserciones intermedias.

**Ejemplo típico:** Lista de productos, lista de usuarios cargada desde una base de datos.

### Creación

```java
ArrayList<String> myList = new ArrayList<>();
```

### Añadir elementos

```java
myList.add("Elemento 1");
myList.add("Elemento 2");
```

### Acceder a elementos

Accede al primer elemento

```java
String element = myList.get(0);
```

### Modificar elementos

Modifica el primer elemento

```java
myList.set(0, "Nuevo Elemento");
```

### Eliminar elementos

Por objeto y por índice

```java
myList.remove("Elemento 1"); 
myList.remove(0);
```

### Tamaño de la lista

```java
int size = myList.size();
```

### Iterar sobre elementos

```java
for (String item : myList) {
    System.out.println(item);
}
```

---

## 2. `LinkedList`

### ¿Qué es?

Una lista donde cada elemento (nodo) tiene una referencia al anterior y al siguiente. Es una lista **doblemente enlazada**.

### ¿Por qué existe?

Porque en `ArrayList`, insertar o eliminar en el medio es lento (se deben mover elementos). `LinkedList` permite hacer eso rápido.

### ¿Para qué sirve?

Cuando necesitas:

* Insertar y eliminar elementos frecuentemente en cualquier parte.
* Recorrer datos hacia adelante o atrás.
* Estructuras tipo pila o cola, pero con más flexibilidad.

**Ejemplo típico:** Editor de texto (cada línea es un nodo), cola de impresión.

### Creación

```java
LinkedList<String> list = new LinkedList<>();
```

### Añadir elementos

```java
list.add("Elemento 1");
list.addFirst("Elemento al inicio");
list.addLast("Elemento al final");
```

### Acceder a elementos

```java
String primerElemento = list.getFirst();
String ultimoElemento = list.getLast();
```

### Modificar elementos

No hay un método directo para reemplazar un elemento en una posición específica sin usar el método set(int index, E element), similar al ArrayList.

```java
list.set(1, "Nuevo Elemento");
```

### Eliminar elementos

```java
list.removeFirst();
list.removeLast();
list.remove("Elemento");
```

> El último ejemplo elimina **la primera ocurrencia** de "Elemento"

### Tamaño de la lista

```java
int size = list.size();
```

### Iterar sobre elementos

```java
for (String item : list) {
    System.out.println(item);
}
```

---

## 3. `ArrayDeque`

### ¿Qué es?

Una **doble cola** que permite insertar y quitar elementos por ambos extremos. Usa un array circular internamente.

### ¿Por qué existe?

Porque `Stack` y `Queue` tradicionales no son tan eficientes ni flexibles. `ArrayDeque` combina lo mejor de ambos.

### ¿Para qué sirve?

Cuando necesitas una **pila** (LIFO) o una **cola** (FIFO), pero más eficiente:

* Reemplaza a `Stack` con mejor rendimiento.
* Reemplaza a `LinkedList` como cola.

**Ejemplo típico:** Implementar un historial (como "deshacer"), o una estructura de control de tareas.

### Creación

```java
ArrayDeque<String> deque = new ArrayDeque<>();
```

### Añadir elementos

```java
deque.addFirst("Elemento al inicio");
deque.addLast("Elemento al final");
```

### Eliminar elementos

```java
deque.removeFirst();
deque.removeLast();
```

### Acceder a elementos

```java
String firstElement = deque.peekFirst();
String lastElement = deque.peekLast();
```

### Uso como pila

```java
deque.push("Nuevo Elemento");
String poppedElement = deque.pop();
```

> Primero se agrega un elemento al inicio de la pila, luego se quita y se retorna.

### Comprobar si está vacío

```java
boolean isEmpty = deque.isEmpty();
```

---

## 4. `PriorityQueue`

### ¿Qué es?

Una cola donde cada elemento tiene una prioridad. Al sacar un elemento, **siempre obtienes el de mayor prioridad** (mínimo por defecto).

### ¿Por qué existe?

Porque a veces no basta con el orden de llegada. Hay tareas más urgentes que otras.

### ¿Para qué sirve?

Ideal cuando necesitas manejar tareas o eventos según su **prioridad**, no su orden de inserción.

**Ejemplo típico:** Sistema de impresión (documentos urgentes), algoritmos de búsqueda como Dijkstra.

### Creación

```java
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();
```

### Añadir elementos

```java
priorityQueue.add(10);
priorityQueue.offer(5);
```

### Acceder al elemento de mayor prioridad

```java
Integer highestPriority = priorityQueue.peek();
```

### Sacar el elemento de mayor prioridad

```java
Integer removedElement = priorityQueue.poll();
```

### Tamaño de la cola

```java
int size = priorityQueue.size();
```

### Iterar sobre elementos
Es importante notar que el iterador no garantiza recorrer los elementos en el orden de prioridad.

```java
for (Integer item : priorityQueue) {
    System.out.println(item);
}
```

---

## 5. `Stack`

### ¿Qué es?

Una estructura de datos tipo **LIFO** (último en entrar, primero en salir). Usada para controlar procesos como una pila de platos.

### ¿Por qué existe?

Para representar estructuras de ejecución o retroceso como llamadas de funciones, navegación hacia atrás, etc.

### ¿Para qué sirve?

* Manejo de llamadas anidadas.
* Evaluación de expresiones matemáticas.
* Implementar "deshacer" o backtracking.

**Ejemplo típico:** Algoritmos recursivos, parsers de código, navegación de páginas.

📌 *Nota:* Es antigua y sincronizada (segura en hilos), por lo que en muchos casos se recomienda `ArrayDeque`.

### Creación

```java
Stack<String> stack = new Stack<>();
```

### Empujar (agregar) elementos

```java
stack.push("Elemento 1");
stack.push("Elemento 2");
```

### Mirar el elemento superior (sin sacarlo)

```java
String topElement = stack.peek();
```

### Sacar elementos

```java
String poppedElement = stack.pop();
```

### Comprobar si la pila está vacía

```java
boolean isEmpty = stack.isEmpty();
```

### Buscar elementos

```java
int position = stack.search("Elemento 1"); 
```

> Devuelve su posición basada en 1 (o -1 si no se encuentra)

---

## 6. `Vector`

### ¿Qué es?

Es similar a `ArrayList`, pero **sincronizado**: es decir, seguro para múltiples hilos que acceden al mismo tiempo.

### ¿Por qué existe?

Fue la primera estructura dinámica en Java antes de que existiera `ArrayList`. Se mantuvo por compatibilidad.

### ¿Para qué sirve?

En contextos **multihilo**, donde necesitas una lista dinámica pero también seguridad.

**Ejemplo típico:** Aplicaciones antiguas, o listas compartidas entre múltiples hilos (aunque hoy se prefiere `Collections.synchronizedList` o `CopyOnWriteArrayList`).

### Creación

```java
Vector<String> vector = new Vector<>();
```

### Añadir elementos

```java
vector.add("Elemento 1");
vector.addElement("Elemento 2");
```

### Acceder a elementos

```java
String elemento = vector.get(0);
```

### Modificar elementos

```java
vector.set(0, "Nuevo Elemento");
```

### Eliminar elementos

```java
vector.remove("Elemento 1");
vector.remove(0);
```

### Tamaño del vector

```java
int size = vector.size();
```

### Iterar sobre elementos

```java
for (String item : vector) {
    System.out.println(item);
}
```

---

## 7. `EnumSet`

### ¿Qué es?

Un conjunto especializado y ultraeficiente para trabajar con valores de tipo `enum`.

### ¿Por qué existe?

Porque los `Set` normales (como `HashSet`) son genéricos y no aprovechan el hecho de que un `enum` tiene un número limitado de valores conocidos.

### ¿Para qué sirve?

Cuando trabajas con **conjuntos de constantes `enum`**, y quieres:

* Eficiencia de espacio y tiempo.
* Operaciones rápidas como unión, intersección.

**Ejemplo típico:** Configurar permisos (lectura, escritura, ejecución), días laborales activos.

```java
EnumSet<Permiso> permisos = EnumSet.of(Permiso.LEER, Permiso.ESCRIBIR);
```

### Creación

```java
EnumSet<DayOfWeek> days = EnumSet.noneOf(DayOfWeek.class);
```

### Añadir elementos

```java
days.add(DayOfWeek.MONDAY);
days.addAll(EnumSet.of(DayOfWeek.TUESDAY, DayOfWeek.WEDNESDAY));
```

### Eliminar elementos

```java
days.remove(DayOfWeek.MONDAY);
days.removeAll(EnumSet.of(DayOfWeek.TUESDAY, DayOfWeek.WEDNESDAY));
```

### Acceso y consulta

```java
boolean contains = days.contains(DayOfWeek.MONDAY);
boolean isEmpty = days.isEmpty();
```

### Iterar sobre elementos

```java
for (DayOfWeek day : days) {
    System.out.println(day);
}
```

---

## Tabla comparativa de estructuras

| Estructura       | Acceso aleatorio | Inserción/Eliminación inicio | Inserción/Eliminación final | Sincronización | Uso ideal                                                                 |
|------------------|------------------|-------------------------------|------------------------------|----------------|---------------------------------------------------------------------------|
| ArrayList        | O(1)             | O(n)                          | Amortiguado O(1)             | No             | Listas con acceso rápido y pocas inserciones/remociones intermedias      |
| LinkedList       | O(n)             | O(1)                          | O(1)                          | No             | Listas con muchas inserciones/eliminaciones en extremos o intermedios    |
| ArrayDeque       | No soportado     | O(1)                          | O(1)                          | No             | Colas/pilas con operaciones rápidas en ambos extremos                    |
| PriorityQueue    | No soportado     | O(log n)                      | O(log n)                      | No             | Colas de prioridad para ordenamiento parcial rápido                      |
| Stack            | No soportado     | O(1)                          | O(1)                          | Sí (legacy)    | Pilas clásicas, aunque se recomienda `Deque` actualmente                 |
| Vector           | O(1)             | O(n)                          | Amortiguado O(1)             | Sí             | Contextos multihilo simples con sincronización automática                |
| EnumSet          | N/A              | N/A                           | N/A                           | No             | Manejo eficiente de conjuntos de enums con operaciones de conjunto       |
