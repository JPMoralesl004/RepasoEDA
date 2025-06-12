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

---

## ¿Para qué sirve?

Es útil en problemas como:

* Resolver **sudokus** o crucigramas.
* Encontrar caminos en **laberintos**.
* Resolver el problema de las **N reinas** (colocar reinas en un tablero sin que se ataquen).
* Generar **combinaciones o permutaciones** (como contraseñas posibles).
* Resolver rompecabezas o juegos de lógica.

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

## ✅ Ventajas del backtracking

* Es una solución general y elegante para muchos problemas complejos.
* Encuentra todas las soluciones si se programa correctamente.

## ❌ Desventajas

* Puede ser **muy lento** si el espacio de soluciones es grande.
* A menudo necesita **optimización** (como poda, memoización) para ser práctico.

---
