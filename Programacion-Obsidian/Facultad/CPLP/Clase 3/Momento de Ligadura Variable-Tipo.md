---
aliases:
  - momento de ligadura variable-tipo
  - static typing
  - dynamic typing
  - tipado estático
  - tipado dinámico
---
El **momento de ligadura variable-tipo** determina cuándo se establece la asociación entre una [[Variable]] y su [[Atributo Tipo|tipo]].

## Estático (static typing)
La [[Ligadura|ligadura]] se especifica en la **declaración** y se realiza en **compilación**. No puede cambiarse en ejecución.

Ejemplos: Pascal, C, C++, Java, Fortran, COBOL, Algol, Simula, ADA.

#### Ventajas
- Variables automáticamente **protegidas** de operaciones ilegales
- **Chequeo de tipos estático** → detección temprana de errores → mayor confiabilidad

#### Formas de declaración

| Forma | Descripción | Ejemplo |
| ----- | ----------- | ------- |
| **Explícita** | Sentencia de declaración | `int x, y;` |
| **Implícita** | Reglas propias del lenguaje | Fortran 77: I-N → enteras |
| **Inferida** | Se deduce del valor asignado (en traducción) | `var sum = 0` → entero |

## Dinámico (dynamic typing)
El tipo se liga en **ejecución** y puede modificarse con sentencias de asignación.

Problemas: comprobación de tipos en runtime, mantenimiento de [[Descriptor|descriptores]], cambios de tamaño en memoria, menor legibilidad.

> Los lenguajes interpretados en general adoptan ligadura dinámica: APL, Snobol, JavaScript, Python, Ruby.

> Ver también: [[Atributo Tipo]], [[Ligadura]], [[Variable]]
