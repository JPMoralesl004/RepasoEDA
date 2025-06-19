# Operaciones Basicas

Las estructuras de datos, como listas, colas, pilas, árboles, etc., existen para manipular datos de manera organizada y eficiente. Pero su poder real viene de lo que podemos hacer con ellas, es decir, de las operaciones básicas:

Independientemente de la estructura de datos que elijamos, necesitamos formas de interactuar con ella. Estas interacciones son las operaciones que realizamos sobre las estructuras de datos. Entender estas operaciones es crucial para utilizar eficazmente cualquier estructura de datos.

---

## ¿Que Son?

Las operaciones básicas sobre estructuras de datos son las acciones fundamentales que podemos realizar en ellas. 

Estas operaciones varían según la estructura, pero algunas comunes incluyen: 

## 1. 🟢 **Inserción (Insertar un dato)**

Consiste en **agregar un nuevo elemento** a la estructura. El lugar de inserción (inicio, medio, final) varía según la estructura.

* En un **array**, insertar en el medio implica mover todos los elementos posteriores → lento.
* En una **lista enlazada**, se puede insertar fácilmente en cualquier parte si conoces la posición.
* En una **pila**, solo se inserta al tope (`push`).
* En una **cola**, solo se inserta al final (`enqueue`).
* En un **árbol**, insertar puede implicar buscar la posición correcta (por ejemplo, en un árbol binario de búsqueda).
* En una **tabla hash**, insertas con una **clave** única.

📌 **Ejemplo real:** Cuando un usuario se registra en una app, se inserta un nuevo registro en la base de datos (estructura de almacenamiento).

---

## 2. 🔴 **Eliminación (Borrar un dato)**

Consiste en **remover un elemento** de la estructura. Esto puede ser más costoso que insertar, según la estructura.

* En un **array**, eliminar un elemento requiere mover otros para llenar el espacio.
* En una **lista enlazada**, se puede eliminar fácilmente si conoces el nodo anterior.
* En una **pila**, se elimina el tope (`pop`).
* En una **cola**, se elimina el primero en entrar (`dequeue`).
* En un **árbol**, eliminar un nodo puede ser complejo (hay que reorganizar subárboles).
* En una **tabla hash**, se elimina por clave.

📌 **Ejemplo real:** Cuando un producto se agota en un sistema de inventario, se elimina o se marca como no disponible.

---

## 3. 🟡 **Búsqueda**

Se refiere a **encontrar si un elemento existe**, y opcionalmente, en qué lugar está.

* En un **array no ordenado**, se debe recorrer todo → `O(n)`
* En un **array ordenado** puedes usar **búsqueda binaria** → `O(log n)`
* En un **hashmap**, buscar por clave es muy rápido → `O(1)`
* En un **árbol binario de búsqueda**, si está balanceado → `O(log n)`

📌 **Ejemplo real:** Buscar un contacto por nombre en tu agenda del teléfono.

---

## 4. 🔵 **Acceso**

Es **obtener directamente** un dato sin recorrer toda la estructura.

* En un **array**, se puede acceder por índice → `O(1)`
* En una **lista enlazada**, hay que recorrer desde el principio → `O(n)`
* En una **tabla hash**, se accede por clave → `O(1)`
* En una **pila o cola**, se accede solo al tope o al frente → no hay acceso aleatorio.

📌 **Ejemplo real:** Obtener el ítem número 5 de una lista de reproducción.

---

## 5. 🟣 **Actualización**

Modificar el valor de un elemento existente.

* En estructuras con acceso rápido (arrays, hashmaps), se actualiza directamente.
* En listas, árboles, etc., primero hay que **buscar el nodo** y luego modificarlo.

📌 **Ejemplo real:** Cambiar tu dirección en un sistema de perfil de usuario.

---

## 6. 🟠 **Recorrido (Traversal)**

Es la acción de **visitar todos los elementos** para analizarlos, imprimirlos o procesarlos.

* En un **array o lista**, se usa un bucle.
* En **árboles**, hay varios recorridos (inorden, preorden, postorden).
* En **grafos**, se usan algoritmos como **BFS** o **DFS**.

📌 **Ejemplo real:** Mostrar todos los mensajes de una conversación en orden cronológico.

---

## 7. ⚪ **Ordenamiento (Sorting)**

No siempre está disponible como operación propia, pero es común aplicar algoritmos de ordenamiento sobre estructuras:

* Bubble Sort, Merge Sort, Quick Sort (en arrays/listas).
* Árboles binarios de búsqueda mantienen los datos ordenados por naturaleza.

📌 **Ejemplo real:** Ordenar productos por precio o por fecha de lanzamiento.

---

## 🧠 ¿Por qué es tan importante conocer esto?

Porque elegir la **estructura de datos correcta** según las operaciones que más vas a realizar hace que tu programa sea:

* **Más rápido** (mejor rendimiento).
* **Más escalable** (soporta más datos).
* **Más claro y mantenible**.

Por ejemplo:

* ¿Harás muchas búsquedas por clave? Usa un **HashMap**.
* ¿Necesitas insertar y eliminar constantemente al inicio o final? Usa una **lista enlazada**.
* ¿Quieres mantener los datos ordenados automáticamente? Usa un **árbol binario de búsqueda**.

---

## ¿Para qué?

- **Manipulación de datos**: Para añadir, eliminar o modificar datos en la estructura.
- **Consulta**: Para recuperar o buscar información específica dentro de la estructura.
- **Organización**: Para mantener la estructura de datos en un estado coherente o en un orden específico.
- **Optimización**: Algunas operaciones, como la ordenación, pueden mejorar la eficiencia de futuras operaciones.
