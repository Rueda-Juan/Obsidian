---
aliases:
  - sintácticas
  - sintaxis
  - sintáctica
---
Es el conjunto de reglas sintácticas y [[Gramática|gramaticales]] que determinan cómo se deben estructurar las instrucciones del [[Lenguaje de Programación|lenguaje]]. Define la forma válida de los programas. Suele describirse mediante gramáticas formales (por ejemplo, [[BNF]] o [[EBNF]]).

#### Elementos que la componen
- **Alfabeto** o conjunto de caracteres
- **Identificadores**
- **Operadores**
- **[[Palabra Reservada|Palabra clave y palabra reservada]]**
- **Comentarios** y uso de blancos

#### Contempla cuestiones de
- Legibilidad
- Verificabilidad
- Traducción
- Falta de ambigüedad

#### Estructura sintáctica

**Vocabulario o words:** conjunto de caracteres y palabras necesarias para construir expresiones, sentencias y programas (identificadores, operadores, palabras claves). Las words no son elementales, se construyen a partir del alfabeto.

**Expresiones:** funciones que a partir de un conjunto de datos devuelven un resultado. Son bloques sintácticos básicos a partir de los cuales se construyen las sentencias y programas.

**Sentencias:** componente sintáctico más importante. Tiene un fuerte impacto en la facilidad de escritura y legibilidad.

#### Reglas léxicas y sintácticas

| Tipo                 | Descripción                                                      | Ejemplo                            |
| -------------------- | ---------------------------------------------------------------- | ---------------------------------- |
| **Reglas léxicas**   | Cómo formar las "words" a partir de los caracteres del alfabeto  | `!=` vs `<>` para "distinto"       |
| **Reglas sintácticas** | Cómo son las sentencias y expresiones                          | En C el `if` no lleva `then`, en Pascal sí |

#### Tipos de sintaxis

| Tipo           | Se refiere a                      |
| -------------- | --------------------------------- |
| **Abstracta**  | La **estructura** del programa    |
| **Concreta**   | La parte **léxica**               |
| **Pragmática** | El **uso práctico**               |

> **Ejemplo:** un `while` en C y en Pascal son **iguales** en sintaxis abstracta (misma estructura: `while condición bloque`) pero **diferentes** en sintaxis concreta (distinto símbolo de distinto, forma de encerrar bloques, uso de paréntesis).

#### Definición de la sintaxis
Se necesita una **descripción finita** para definir un conjunto infinito (el conjunto de todos los programas bien escritos). Ver: [[Gramática]], [[BNF]], [[EBNF]], [[Diagramas Sintácticos]].
