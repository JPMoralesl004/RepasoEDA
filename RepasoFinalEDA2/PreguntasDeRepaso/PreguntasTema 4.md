# Ordenacion
---

## Preguntas Generales

### ¿Cuál es la diferencia entre algoritmos de ordenación internos y externos?

* Los algoritmos **internos** realizan el ordenamiento completamente en memoria RAM. Los **externos** manejan grandes volúmenes de datos que no caben en memoria, accediendo al almacenamiento externo (como disco duro).

### ¿Qué características definen a un algoritmo de ordenación estable?

* Un algoritmo es **estable** si mantiene el **orden relativo de los elementos iguales**. Esto es importante cuando hay varios campos y el orden por un campo debe preservar el orden previo por otro.

### ¿Qué factores influyen en la elección del algoritmo de ordenación más adecuado para un problema?

* Volumen de datos
* Si ya está parcialmente ordenado
* Necesidad de estabilidad
* Restricciones de espacio/memoria
* Velocidad requerida y complejidad esperada

---

## Bubble Sort

### ¿Es Bubble Sort un algoritmo estable?

* Sí, **Bubble Sort es estable** porque no intercambia elementos iguales entre sí, conservando su orden original.

### ¿Qué casos hacen que Bubble Sort sea ineficiente?

* Cuando el array está muy desordenado. Su rendimiento es **O(n²)** en la mayoría de los casos.

### ¿Cuándo sería aceptable usar Bubble Sort, a pesar de su ineficiencia?

* En casos educativos, arreglos muy pequeños o cuando la simplicidad del código prima sobre el rendimiento.

---

## Bucket Sort

### ¿Cómo divide Bucket Sort los datos para realizar el ordenamiento?

* Distribuye los elementos en diferentes “cubos” o buckets según su valor, luego ordena cada bucket (usualmente con otro algoritmo) y los concatena.

### ¿Qué supuestos deben cumplirse para que Bucket Sort sea eficiente?

* Que los datos estén distribuidos **uniformemente** sobre un rango conocido, y que se puedan asignar a buckets de forma equitativa.

### ¿En qué escenarios concretos es ideal usar Bucket Sort?

* Datos decimales distribuidos uniformemente (como números entre 0 y 1), grandes volúmenes donde se busca eficiencia lineal.

---

## Counting Sort

### ¿Cómo funciona Counting Sort y cómo utiliza arreglos auxiliares?

* Cuenta cuántas veces aparece cada valor y usa esa información para colocar cada elemento en su posición final. Utiliza un array auxiliar para el conteo.

### ¿Por qué Counting Sort no es adecuado para ordenar datos con valores muy dispersos?

* Porque necesita un array auxiliar de tamaño proporcional al **rango máximo de los valores**. Si el rango es muy grande, se desperdicia memoria.

### ¿Se puede aplicar Counting Sort a datos no numéricos?

* No directamente. Pero sí se puede adaptar usando códigos ASCII u otros índices numéricos equivalentes si hay un rango discreto limitado.

---

## Radix Sort

### ¿Qué principio sigue Radix Sort para ordenar números?

* Ordena los números dígito a dígito, desde el dígito menos significativo al más significativo (LSD) o al revés (MSD).

### ¿Qué rol juega el ordenamiento estable dentro de Radix Sort?

* Radix Sort **depende de algoritmos estables** en cada paso para preservar el orden de los dígitos previamente ordenados.

### ¿Cuál es la diferencia entre Least Significant Digit (LSD) y Most Significant Digit (MSD) en Radix Sort?

* LSD comienza por el **dígito menos significativo** (derecha).
* MSD comienza por el **más significativo** (izquierda), lo que puede mejorar rendimiento si se interrumpe antes.

### ¿Qué tipo de datos son ideales para ordenar con Radix Sort?

* Números enteros o cadenas de longitud fija, especialmente cuando el rango de dígitos es limitado (por ejemplo, 0–9).

---

## Heap Sort

### ¿Cómo se construye un heap en Heap Sort?

* Se construye un **montículo máximo (max-heap)** reorganizando los elementos, luego se extrae el máximo y se reconstruye el heap.

### ¿Qué operaciones principales se realizan en Heap Sort?

* **Heapify** (crear el heap) y **extraer el máximo**, que se repite hasta ordenar todo el arreglo.

### ¿Qué ventajas y desventajas tiene Heap Sort respecto a Merge Sort?

* Ventaja: no necesita espacio extra (in-place).
* Desventaja: **no es estable** y tiene más operaciones por elemento, por lo que puede ser más lento que Merge Sort en la práctica.

---

## Insertion Sort

### ¿Cómo ordena los elementos el algoritmo de Insertion Sort?

* Inserta cada elemento en la posición correcta de un subconjunto ordenado (como barajar cartas).

### ¿Cuál es la ventaja de Insertion Sort en arrays casi ordenados?

* Tiene rendimiento **cercano a O(n)** en arrays casi ordenados, muy eficiente en ese caso.

### ¿Dónde se usa comúnmente Insertion Sort en aplicaciones reales?

* En arreglos pequeños o como parte de algoritmos híbridos (como IntroSort), para ordenamientos locales o simples.

---

## Intro Sort

### ¿Qué es Intro Sort y qué lo hace diferente de otros algoritmos?

* Es un algoritmo híbrido que **comienza con QuickSort**, cambia a **HeapSort** si la recursión se hace profunda, y termina con **Insertion Sort** en pequeños subconjuntos.

### ¿Qué combinación de algoritmos usa Internamente Intro Sort?

* QuickSort, HeapSort y Insertion Sort.

### ¿Cómo se decide cuándo cambiar de Quick Sort a Heap Sort en Intro Sort?

* Se establece una **profundidad límite** (por ejemplo, log₂(n)×2). Si se alcanza, se cambia a HeapSort para evitar el peor caso de QuickSort.

### ¿Dónde se usa comúnmente Intro Sort en bibliotecas estándar?

* Es el algoritmo por defecto en **C++ STL (`std::sort`)** y otros entornos modernos donde se busca lo mejor de varios mundos.

---

## Merge Sort

### ¿Por qué Merge Sort es estable y cuándo es preferido?

* Es estable porque al combinar arreglos mantiene el orden original de elementos iguales. Se prefiere en listas vinculadas y cuando se requiere estabilidad.

### ¿Merge Sort es mejor que Quick Sort en qué escenarios?

* Cuando se necesita **estabilidad**, en arreglos muy grandes o en estructuras que se beneficien de acceso secuencial (listas enlazadas).


### ¿Puede Merge Sort funcionar bien en arreglos muy grandes? ¿Por qué?

* Sí, especialmente en algoritmos externos donde los datos no caben en memoria, ya que permite fragmentar y combinar secuencialmente.

---

## Quick Sort

### ¿Cómo selecciona el pivote Quick Sort y cómo afecta su rendimiento?

* Puede seleccionar el pivote como el primer, último, central o aleatorio. Una mala elección (como siempre el primero en arreglo ordenado) puede llevar al **peor caso** O(n²).


### ¿Cuál es la complejidad temporal en el peor caso y cómo evitarlo?

* El peor caso es **O(n²)**, pero puede evitarse con técnicas como **pivote aleatorio** o usando **IntroSort** como mejora.


### ¿Qué técnicas se usan para mejorar el rendimiento de Quick Sort?

* Uso de pivotes aleatorios o “mediana de tres”, limitar la recursión, y cambiar a Insertion Sort para subarreglos pequeños.

### ¿Qué escenarios hacen a Quick Sort más eficiente que Merge Sort?

* En arreglos en memoria, sin necesidad de estabilidad, QuickSort es generalmente más rápido por ser **in-place** y tener menos uso de memoria.

---

## Selection Sort

### ¿Cómo funciona Selection Sort y cuántas comparaciones hace?

* Encuentra el mínimo y lo coloca en la posición correcta, repitiendo para el resto. Hace **n² comparaciones** siempre.

### ¿Cuál es su rendimiento comparado con Insertion o Bubble Sort?

* Similar o peor. Aunque realiza menos intercambios que Bubble, tiene el mismo número de comparaciones que los otros dos.

### ¿Cuáles son sus ventajas y desventajas principales?

* Ventajas: fácil de implementar, mínimo número de intercambios.
* Desventajas: **ineficiente para listas grandes**, siempre realiza muchas comparaciones.

### ¿Se recomienda para arreglos pequeños o grandes? ¿Por qué?

* Solo para **arreglos muy pequeños** o educativos, ya que su complejidad **O(n²)** lo hace ineficiente en producción.

---
