# Estructura de Datos

Las **estructuras de datos** son formas organizadas de almacenar y gestionar datos en una computadora para que puedan ser utilizados de manera eficiente. Permiten guardar, acceder, modificar y 
eliminar datos según las necesidades de un programa o algoritmo.

---

## Clasificación general

1. **Estructuras de datos primitivas**:

   * Son las más básicas.
   * Ejemplos: enteros (`int`), flotantes (`float`), caracteres (`char`), booleanos (`bool`).

2. **Estructuras de datos no primitivas**:

   * Se basan en las primitivas para organizar conjuntos de datos más complejos.
   * Se dividen en:

   #### a) **Lineales**:

   * Los elementos están organizados uno tras otro.
   * Ejemplos:

     * **Arreglos (arrays)**: colección de elementos del mismo tipo, accesibles por índices.
     * **Listas enlazadas**: cada elemento apunta al siguiente.
     * **Pilas (stacks)**: siguen el principio LIFO (último en entrar, primero en salir).
     * **Colas (queues)**: siguen el principio FIFO (primero en entrar, primero en salir).

   #### b) **No lineales**:

   * Los datos no se organizan secuencialmente.
   * Ejemplos:

     * **Árboles**: como los árboles binarios, donde cada nodo tiene hijos.
     * **Grafos**: estructuras que modelan relaciones entre elementos (nodos y aristas).

   #### c) **Estructuras asociativas**:

   * Relacionan una clave con un valor.
   * Ejemplos:

     * **Tablas hash / Diccionarios / Mapas**: permiten acceso rápido mediante claves únicas.

### ¿Para qué se usan?

* Para optimizar el rendimiento de algoritmos.
* Para facilitar tareas como búsqueda, ordenamiento, recorrido, almacenamiento eficiente, etc.

---

## ¿Por que son importantes?

Las **estructuras de datos son fundamentales** en informática y programación porque:

---

### 1. **Organizan los datos de forma eficiente**

* Permiten guardar y acceder a la información de manera óptima.
* Ejemplo: buscar un elemento en una **tabla hash** es mucho más rápido que buscarlo en una lista simple.


### 2. **Mejoran el rendimiento del software**

* Elegir la estructura adecuada puede reducir el tiempo y el uso de memoria.
* Un **algoritmo de búsqueda** en un **árbol balanceado** es mucho más eficiente que en una lista desordenada.


### 3. **Facilitan la resolución de problemas complejos**

* Muchas soluciones de programación (como redes sociales, sistemas bancarios, motores de búsqueda) dependen de estructuras como **grafos**, **pilas**, o **colas de prioridad**.


### 4. **Son la base de los algoritmos**

* Algoritmos de ordenamiento, búsqueda, recorrido, etc., dependen directamente de estructuras como arreglos, listas, árboles y más.


### 5. **Permiten modularidad y reutilización**

* Una buena estructura de datos puede reutilizarse en distintos contextos sin modificar su funcionamiento interno.


### 6. **Son clave en entrevistas técnicas y desarrollo profesional**

* Las empresas tecnológicas evalúan el dominio de estructuras de datos porque demuestran capacidad lógica, de análisis y solución eficiente de problemas.

---

## ¿Como funcionan?

El **funcionamiento de una estructura de datos** depende del tipo que se use, pero todas cumplen con un objetivo común: **almacenar, organizar y manipular datos de forma eficiente**.

---

## 🔹 1. **Arreglos (Arrays)**

* **Cómo funcionan**: Guardan datos en **posiciones consecutivas de memoria**.
* Cada elemento se accede mediante un índice, empezando desde 0.
* **Acceso** rápido, pero **inserción/eliminación** puede ser costosa (hay que mover elementos).

---

*Java*

```java
public class EjemploArray {
    public static void main(String[] args) {
        int[] numeros = {10, 20, 30};
        System.out.println(numeros[1]);  // Imprime 20
    }
}
```

---

*Python*

```python
numeros = [10, 20, 30]
print(numeros[1])  # Imprime 20
```

---

## 🔹 2. **Listas enlazadas**

* Cada elemento (nodo) tiene un **valor** y una **referencia al siguiente**.
* Inserciones/eliminaciones son eficientes, pero el acceso es más lento (hay que recorrer uno por uno).

---

*Java*

```java
class Nodo {
    int valor;
    Nodo siguiente;

    public Nodo(int valor) {
        this.valor = valor;
        this.siguiente = null;
    }
}

public class ListaEnlazada {
    public static void main(String[] args) {
        Nodo n1 = new Nodo(10);
        Nodo n2 = new Nodo(20);
        n1.siguiente = n2;

        System.out.println(n1.siguiente.valor);  // Imprime 20
    }
}
```

---

*Python*

```python
class Nodo:
    def __init__(self, valor):
        self.valor = valor
        self.siguiente = None

n1 = Nodo(10)
n2 = Nodo(20)
n1.siguiente = n2  # Enlaza n1 con n2
```

---

## 🔹 3. **Pilas (Stacks)**

* Funcionan con el principio **LIFO** (Last In, First Out).
* Solo puedes agregar o quitar elementos desde el tope.

---

*Java*

```java
import java.util.Stack;

public class EjemploPila {
    public static void main(String[] args) {
        Stack<Integer> pila = new Stack<>();
        pila.push(1);
        pila.push(2);
        System.out.println(pila.pop());  // Imprime 2
    }
}
```

---

*Python*

```python
pila = []
pila.append(1)  # push
pila.append(2)
print(pila.pop())  # Imprime 2 (último en entrar, primero en salir)
```

---

## 🔹 4. **Colas (Queues)**

* Funcionan con el principio **FIFO** (First In, First Out).
* El primer elemento en entrar es el primero en salir.

---

*Java*

```java
import java.util.LinkedList;
import java.util.Queue;

public class EjemploCola {
    public static void main(String[] args) {
        Queue<Integer> cola = new LinkedList<>();
        cola.add(1);
        cola.add(2);
        System.out.println(cola.poll());  // Imprime 1
    }
}
```

---

*Python*


```python
from collections import deque

cola = deque()
cola.append(1)
cola.append(2)
print(cola.popleft())  # Imprime 1
```

---

## 🔹 5. **Árboles**

* Cada nodo tiene un valor y referencias a uno o más hijos.
* Muy usados para representar jerarquías y búsquedas rápidas (como árboles binarios de búsqueda).

---

*java*

```java
class Nodo {
    int valor;
    Nodo izq, der;

    public Nodo(int valor) {
        this.valor = valor;
        izq = der = null;
    }
}

public class ArbolBinario {
    public static void main(String[] args) {
        Nodo raiz = new Nodo(10);
        raiz.izq = new Nodo(5);
        raiz.der = new Nodo(15);

        System.out.println(raiz.izq.valor);  // Imprime 5
    }
}
```

---

*Python*

```python
class Nodo:
    def __init__(self, valor):
        self.valor = valor
        self.izq = None
        self.der = None
```

---

## 🔹 6. **Tablas hash (diccionarios/mapas)**

* Usan una **clave única** para acceder directamente al valor.
* Muy rápidos para buscar, insertar o eliminar datos.

---

*Java*

```java
import java.util.HashMap;

public class EjemploHashMap {
    public static void main(String[] args) {
        HashMap<String, Integer> edades = new HashMap<>();
        edades.put("Ana", 20);
        edades.put("Luis", 30);

        System.out.println(edades.get("Luis"));  // Imprime 30
    }
}
```

---

```python
edades = {"Ana": 20, "Luis": 30}
print(edades["Luis"])  # Imprime 30
```

---

### En resumen:

Cada estructura tiene un **mecanismo interno distinto** (uso de índices, punteros, claves, etc.), pero todas permiten realizar operaciones como:

* **Insertar datos**
* **Eliminar datos**
* **Buscar datos**
* **Actualizar datos**

---
