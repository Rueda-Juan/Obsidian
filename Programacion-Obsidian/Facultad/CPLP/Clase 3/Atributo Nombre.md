---
aliases:
  - nombre
  - atributo nombre
---
El **nombre** es el string de caracteres que se usa para referenciar a una [[Variable]] (identificador). Se introduce mediante una sentencia de declaración.

#### Aspectos de diseño

**Longitud máxima:**

| Lenguaje | Longitud |
| -------- | -------- |
| Fortran | 6 caracteres |
| C | Depende del compilador (suele ser 32) |
| Python, Pascal, Java, ADA | Cualquier longitud |

**Caracteres aceptados:**

| Lenguaje | Reglas |
| -------- | ------ |
| Python, C, Pascal | `_` permitido |
| Ruby | Solo minúsculas para locales; `$` para globales |

**Sensibilidad a mayúsculas:**
- C, C++, Java, Python: sensibles (`Sum ≠ sum`)
- Pascal: no sensible

> Ver también: [[Variable]], [[Palabra Reservada]], [[Atributo Alcance]]
