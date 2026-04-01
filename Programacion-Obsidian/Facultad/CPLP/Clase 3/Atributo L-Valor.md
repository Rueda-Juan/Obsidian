---
aliases:
  - L-valor
  - l-valor
  - l-value
  - atributo l-valor
---
El **L-valor** de una [[Variable]] es la **dirección del área de memoria** ligada a la variable durante la ejecución. Las instrucciones del programa acceden a la variable por su L-valor.

#### [[Tiempo de Vida]] (lifetime)
Es el tiempo en que la variable está **alocada en memoria** y en el cual el binding existe. Desde que se solicita hasta que se libera.

#### [[Alocación de Memoria|Tipos de alocación]]

| Tipo | Momento | Comportamiento |
| ---- | ------- | -------------- |
| **Estática** | Compilación | Perdura hasta fin de ejecución |
| **Dinámica automática** | Ejecución (al aparecer declaración) | Se libera al salir del ámbito |
| **Dinámica explícita** | Ejecución (por el programador) | `new`, punteros |
| **Persistente** | Más allá de la ejecución | Archivos, bases de datos |

#### `extern` y `static` en C
- `extern`: extiende el alcance de una variable a otro archivo
- `static` en función: [[Tiempo de Vida|tiempo de vida]] = todo el programa; [[Atributo Alcance|alcance]] = solo la función
- `static` fuera de función: alcance hasta el final del archivo, no se puede extender con `extern`

> Ver también: [[Variable]], [[Atributo R-Valor]], [[Alocación de Memoria]]
