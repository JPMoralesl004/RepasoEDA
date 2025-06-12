# Backtracking 

---

El backtracking es una técnica algorítmica que utiliza la recursividad para construir soluciones incrementalmente, abandonando caminos que se determina no conducirán a una solución válida.

---

### Definición formal

El backtracking es una estrategia algorítmica para encontrar soluciones a problemas computacionales, particularmente aquellos que requieren satisfacer restricciones, mediante la construcción 
incremental de candidatos a solución y el abandono de candidatos parciales ("backtrack" o retroceso) tan pronto como se determina que no pueden extenderse a una solución válida.

---

## ¿Cómo funciona?

1. Se explora una posible solución **paso a paso**.
2. En cada paso se **verifica si es válida** (parcial o total).
3. Si no es válida, se **retrocede** (backtrack) y se intenta otra alternativa.
4. Se repite hasta encontrar una solución o agotar todas las opciones.

---

## ¿Cuándo se usa?

Usa **backtracking** cuando:

* El problema requiere **explorar múltiples combinaciones o caminos**.
* Hay muchas posibles soluciones y necesitas encontrar **una, todas o la mejor**.
* No se puede usar un algoritmo directo o codicioso porque hay que considerar más de una opción por paso.

### Elementos fundamentales

- **Estado parcial**: Representación de una solución parcial o incompleta al problema.
- **Restricciones**: Condiciones que deben cumplirse para que una solución sea válida.
- **Verificación de validez**: Mecanismo para determinar si un estado parcial puede extenderse a una solución válida.
- **Mecanismo de retroceso**: Proceso de abandonar un camino de exploración cuando se determina que no conducirá a una solución válida.

### Estructura general

Todo algoritmo de backtracking sigue una estructura recursiva con estos componentes:

1. **Verificación de caso base**: Determinar si se ha alcanzado una solución completa.
2. **Generación de candidatos**: Identificar las posibles extensiones del estado actual.
3. **Verificación de restricciones**: Comprobar si una extensión particular viola alguna restricción.
4. **Recursión con estado modificado**: Avanzar recursivamente con la extensión seleccionada.
5. **Retroceso**: Deshacer modificaciones y probar otras alternativas cuando una rama no lleva a solución.

---

## ¿Para qué sirve?

Es útil en problemas como:

* Resolver **sudokus** o crucigramas.
* Encontrar caminos en **laberintos**.
* Resolver el problema de las **N reinas** (colocar reinas en un tablero sin que se ataquen).
* Generar **combinaciones o permutaciones** (como contraseñas posibles).
* Resolver rompecabezas o juegos de lógica.

### Diferencia con otras técnicas recursivas

El backtracking se distingue de la recursividad simple por:

|Característica|Recursividad simple|Backtracking|
|-|-|-|
|Enfoque|Divide el problema en casos más pequeños|Construye soluciones incrementalmente y prueba alternativas|
|Ramificación|Generalmente fija|Dinámica, se reduce mediante poda|
|Exploración|Completa todo el árbol recursivo|Abandona ramas tan pronto como se detectan como inviables|
|Uso de estado|Generalmente no mantiene estado entre llamadas|Mantiene y actualiza estado para rastrear soluciones parciales|
|Caso típico|Cálculos matemáticos como factorial o Fibonacci|Problemas de restricciones como N-Reinas o coloración de grafos|

---

## Ejemplo: El problema de las N reinas

Colocar `N` reinas en un tablero de ajedrez `NxN` sin que se ataquen entre sí.

```java
void resolver(int fila) {
    if (fila == N) {
        mostrarSolucion();
        return;
    }
    for (int columna = 0; columna < N; columna++) {
        if (esSeguro(fila, columna)) {
            ponerReina(fila, columna);
            resolver(fila + 1);          // llamada recursiva (profundizar)
            quitarReina(fila, columna);  // backtrack (retroceder)
        }
    }
}
```

* Se prueba colocar una reina en cada columna de cada fila.
* Si colocar una reina lleva a un conflicto más adelante, se quita y se prueba otra posición.
* Se exploran todas las configuraciones posibles.

---

## ✅ Ventajas

* Es una solución general y elegante para muchos problemas complejos.
* Encuentra todas las soluciones si se programa correctamente.

## ❌ Desventajas

* Puede ser **muy lento** si el espacio de soluciones es grande.
* A menudo necesita **optimización** (como poda, memoización) para ser práctico.

---
