# Tabla comparativa de estructuras

| Estructura       | Acceso aleatorio | Inserción/Eliminación inicio | Inserción/Eliminación final | Sincronización | Uso ideal                                                                 |
|------------------|------------------|-------------------------------|------------------------------|----------------|---------------------------------------------------------------------------|
| ArrayList        | O(1)             | O(n)                          | Amortiguado O(1)             | No             | Listas con acceso rápido y pocas inserciones/remociones intermedias      |
| LinkedList       | O(n)             | O(1)                          | O(1)                          | No             | Listas con muchas inserciones/eliminaciones en extremos o intermedios    |
| ArrayDeque       | No soportado     | O(1)                          | O(1)                          | No             | Colas/pilas con operaciones rápidas en ambos extremos                    |
| PriorityQueue    | No soportado     | O(log n)                      | O(log n)                      | No             | Colas de prioridad para ordenamiento parcial rápido                      |
| Stack            | No soportado     | O(1)                          | O(1)                          | Sí (legacy)    | Pilas clásicas, aunque se recomienda `Deque` actualmente                 |
| Vector           | O(1)             | O(n)                          | Amortiguado O(1)             | Sí             | Contextos multihilo simples con sincronización automática                |
| EnumSet          | N/A              | N/A                           | N/A                           | No             | Manejo eficiente de conjuntos de enums con operaciones de conjunto       |
