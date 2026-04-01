---
aliases:
  - alocación de memoria
  - alocación
  - memoria
---
La **alocación de memoria** es el momento en que se reserva memoria para una [[Variable]]. Determina el [[Tiempo de Vida]] de la variable.

#### Tipos de alocación

| Tipo | Momento | Comportamiento | Ejemplo |
| ---- | ------- | -------------- | ------- |
| **Estática** | Compilación | En zona de datos, perdura hasta fin de ejecución. Sensible a la historia | Variables globales, `static` en C |
| **Dinámica automática** | Ejecución | Cuando aparece la declaración; se libera al salir del ámbito | Variables locales en funciones |
| **Semidinámica** | Ejecución | El tamaño se determina en ejecución pero no cambia una vez alocado | Arreglos semidinámicos en Ada |
| **Dinámica explícita** | Ejecución | Requerida por el programador con un constructor | `new` en Pascal/C++, `malloc` en C |
| **Persistente** | Más allá de la ejecución | No tiene relación con el tiempo de ejecución del programa | Archivos, bases de datos |

> Ver también: [[Atributo L-Valor]], [[Tiempo de Vida]], [[Variable]]
