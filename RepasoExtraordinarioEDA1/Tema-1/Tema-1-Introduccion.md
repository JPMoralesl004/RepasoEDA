# Primitivas, matrices, clases & objetos

---

## Tipos primitivos

Recordemos el concepto de variables [visto en Programación 1](https://github.com/mmasias/23-24-prg1/blob/main/temario/variables.md)

|Tipos primitivos|
|-|
<img src="https://raw.githubusercontent.com/mmasias/23-24-prg1/e6aa945f3bbb90999a22d0894d17f021309bb156/imagenes/modelosUML/tiposPrimitivos.svg" />

---

- Declarar una variable de tipo primitivo implica:
  1. Reservar una dirección en memoria.
  1. Reservar los bytes en función al tipo.

<div align=center>

|Variable|Dirección/Ref|Valor|
|-|-|-|
precio|0x7C000000|568
copiaPrecio|0x7C000008|568

</div>

---

## Datos estructurados

### ¿Qué son los **Datos Estructurados**?

Son datos **organizados** de manera que se puedan **gestionar, acceder y procesar eficientemente**. En programación (y especialmente en Java), los datos estructurados se almacenan en **estructuras de datos**, 
que pueden ser:

| Tipo de estructura | Descripción breve                                    |
| ------------------ | ---------------------------------------------------- |
| **Array (matriz)** | Colección de elementos del mismo tipo, en orden fijo |
| **Lista**          | Conjunto de elementos ordenados, tamaño variable     |
| **Pila (Stack)**   | LIFO: Último en entrar, primero en salir             |
| **Cola (Queue)**   | FIFO: Primero en entrar, primero en salir            |
| **Árbol**          | Estructura jerárquica (como un árbol genealógico)    |
| **Grafo**          | Conjunto de nodos conectados por aristas             |

---

### Ejemplo: Datos estructurados en Java

Supongamos que tienes que guardar información de estudiantes: nombre, edad, nota.

Podrías usar una **clase** (estructura propia) para organizar esos datos:

```java
public class Estudiante {
    String nombre;
    int edad;
    double nota;
}
```

Luego, usar un **array** o una **lista** para almacenar muchos estudiantes:

```java
Estudiante[] estudiantes = new Estudiante[30]; // array estructurado
```

O mejor aún:

```java
ArrayList<Estudiante> estudiantes = new ArrayList<>(); // lista dinámica
```

---

### ¿Por qué son importantes?

1. **Facilitan el almacenamiento lógico y ordenado de la información.**
2. **Permiten aplicar algoritmos para buscar, ordenar, recorrer, etc.**
3. **Sientan la base para resolver problemas más complejos.**

---

### Relación con conceptos previos:

* **Primitivas**: Son los bloques base de los datos estructurados.
* **Arrays y listas**: Son los ejemplos más comunes de datos estructurados.
* **Clases y objetos**: Se usan para crear estructuras más avanzadas (como listas enlazadas, árboles, etc.).

---

### Strings, matrices, clases & objetos...

```java
String cadenaTexto = "Una cadena";
String otraCadena = cadenaTexto;
String terceraCadena = "Una cadena";
```

<div align=center>

|Variable|Dirección/Ref|Valor|
|-|:-:|:-:|
||0x7C000000|"Una cadena"|
cadenaTexto|0x7C000900|0x7C000000
otraCadena|0x7C009999|0x7C000000
||0x7C008888|"Una cadena"|
terceraCadena|0x7C066666|0x7C008888

</div>

#### String & StringBuilder

[Breve revisión del tema](stringStringBuilder.md)

### Prácticum

Lo mejor es verlo y discutirlo en vivo, sobre uno o varios ejemplos.

<div align=center>

|Java|Python|JavaScript|PHP
|-|-|-|-|
|[Varias situaciones](/src/Tema001/Tema001.java)|[Ídem](/src/Tema001/Tema001.py)|[Ídem](/src/Tema001/Tema001.js)|[Ídem](/src/Tema001/Tema001.php)
[Array 2D, 🤔](/src/Tema001/Tema001Arrays2D.java)

</div>
