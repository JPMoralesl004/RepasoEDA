# Orden en Recursividad

---

## Definición

En el contexto de la recursividad, el **orden** hace referencia a la **secuencia lógica y temporal** en la que se ejecutan las llamadas recursivas y se resuelven sus resultados. Este orden está determinado por la estructura de la función recursiva y por el comportamiento de la **pila de llamadas (call stack)** del lenguaje de programación.

Existen dos fases principales:

1. **Fase descendente (de llamada):**
   Es el proceso mediante el cual se realizan las llamadas recursivas, cada una empujando un nuevo contexto de ejecución a la pila. Este proceso continúa hasta alcanzar una condición base que detiene la recursividad.

2. **Fase ascendente (de retorno):**
   Comienza cuando se alcanza el caso base. A partir de ese punto, las llamadas recursivas se **resuelven en orden inverso** al que fueron realizadas, desenrollando la pila y combinando los resultados parciales para construir la solución final.

Este doble flujo determina el orden de evaluación y permite implementar estrategias como:

* **Preorden:** procesamiento antes de la llamada recursiva.
* **Postorden:** procesamiento después de la llamada recursiva.
* **Inorden:** procesamiento intercalado entre llamadas recursivas (común en estructuras binarias).

---
