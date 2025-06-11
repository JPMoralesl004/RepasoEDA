# Inmutabilidad

---

## Preguntas Generales sobre Inmutabilidad

### ¿Qué implicaciones tiene la inmutabilidad para el diseño de software multihilo?

* La inmutabilidad simplifica el diseño concurrente porque los objetos no pueden cambiar su estado. Esto elimina la necesidad de sincronización, ya que múltiples hilos pueden acceder simultáneamente a los mismos datos sin riesgo de condiciones de carrera.

### ¿Qué diferencias prácticas hay entre inmutabilidad “superficial” y “profunda”?

* La inmutabilidad **superficial** implica que la referencia del objeto no cambia, pero sus campos internos podrían ser mutables. La **profunda** asegura que ni el objeto ni sus componentes internos cambian, protegiendo completamente el estado.

### ¿En qué escenarios la inmutabilidad puede ser contraproducente?

* Puede ser contraproducente en contextos donde hay muchas modificaciones frecuentes sobre grandes estructuras de datos, ya que cada cambio implica la creación de una nueva copia, lo que puede impactar el rendimiento y el uso de memoria.

### ¿Qué técnicas existen para manejar estructuras de datos grandes de forma eficiente en un contexto inmutable?

* Se pueden usar estructuras de datos **persistentes** (como en lenguajes funcionales), **copy-on-write**, y librerías como `Guava` o `Vavr` en Java que optimizan la reutilización de datos entre versiones sin copias completas.

---

## Conceptos Avanzados de Inmutabilidad

### ¿Cómo se puede garantizar la inmutabilidad de una clase que contiene referencias a objetos mutables?

* Usando **copias defensivas** al asignar los objetos y al devolverlos desde los métodos getters. Además, asegurarse de que los campos sean `private final` y que no se expongan referencias mutables.

### ¿Cómo se implementa una clase completamente inmutable en Java?

* Declarando la clase `final` para evitar herencia, marcando todos los campos como `private final`, inicializando todos los campos en el constructor, evitando setters, y usando copias defensivas para campos que son colecciones o referencias mutables.

### ¿Cuál es el papel de las clases `final`, los campos `final`, y las copias defensivas en la inmutabilidad?

* `final` en clases evita la herencia que pueda modificar comportamiento. `final` en campos garantiza que no se reasignen. Las **copias defensivas** protegen de mutaciones externas, asegurando que el estado no cambie una vez construido.

### ¿Se puede aplicar el patrón Builder en clases inmutables sin romper el principio?

* Sí. El patrón Builder puede usarse para construir objetos inmutables. El Builder mantiene estado mutable internamente, pero el objeto final construido es inmutable, ya que se genera una instancia con valores fijos y sin setters.

---

## Operaciones Funcionales sobre Colecciones Inmutables

### ¿Qué ventajas ofrece aplicar operaciones funcionales (map, filter, reduce) sobre colecciones inmutables?

* Las operaciones funcionales sobre colecciones inmutables son **declarativas**, sin efectos colaterales, fáciles de componer y seguras para concurrencia. Permiten escribir código más expresivo y mantenible.

### ¿Cómo se transforman estructuras inmutables sin violar la inmutabilidad?

* En lugar de modificar la estructura, se devuelve una **nueva versión modificada** con los cambios aplicados. Ejemplo: `List<T> newList = oldList.stream().filter(...).collect(Collectors.toList())`.

### ¿Cuál es la diferencia conceptual entre modificar y transformar una colección?

* Modificar implica **cambiar el estado actual** de la colección original (paradigma imperativo). Transformar implica **crear una nueva versión** basada en la colección original, manteniéndola intacta (paradigma funcional).

### ¿Qué impacto tiene el uso de colecciones inmutables en el rendimiento de aplicaciones que procesan grandes volúmenes de datos?

* Puede aumentar la presión de memoria si se crean muchas copias. Sin embargo, usando estructuras de datos **persistentes** (como árboles compartidos), o técnicas de reutilización de memoria, se mitiga el impacto. También mejora la paralelización y evita errores por mutaciones.

---

## Fundamentos de Objetos Inmutables

### ¿Cuáles son los requisitos mínimos para que una clase sea considerada inmutable en Java?

* La clase debe ser `final`, los campos `private final`, inicializados solo en el constructor, sin setters, y proteger cualquier campo mutable mediante copias defensivas o referencias a objetos inmutables.

### ¿Qué patrón de diseño puede ayudar a construir objetos inmutables con múltiples propiedades?

* El **Builder Pattern** permite construir objetos inmutables paso a paso, especialmente cuando hay muchos campos opcionales. Al final se crea una instancia completamente inmutable.

### ¿Qué problemas puede presentar el uso de objetos inmutables en entornos donde el estado debe evolucionar?

* Puede dificultar la actualización frecuente de datos, ya que cada cambio requiere crear una nueva instancia. Esto puede afectar el rendimiento o generar gran número de objetos intermedios si no se optimiza adecuadamente.

### ¿Cómo se maneja el versionamiento de objetos inmutables sin perder rendimiento ni claridad?

* Usando técnicas como **versionado explícito** (cada versión tiene su ID o marca de tiempo), y **estructuras compartidas** donde los objetos comparten partes comunes internamente para evitar duplicaciones innecesarias de datos.

---
