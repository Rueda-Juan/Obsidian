---
aliases:
  - alcance estático
  - alcance léxico
  - static scope
---
El **alcance estático** (o alcance léxico) define el alcance de una [[Variable]] en términos de la **estructura léxica del programa**. Se puede determinar examinando el texto del programa, **sin necesidad de ejecutarlo**.

> La mayoría de los lenguajes adoptan reglas de alcance estático: C, Pascal, ADA, Python, Java.

#### Regla de búsqueda
Si una unidad necesita referenciar una variable no declarada localmente, debe buscarla siguiendo la **estructura del programa** hacia las unidades más externas donde está **contenida**.

#### Reglas específicas por lenguaje

| Lenguaje | Regla particular |
| -------- | ---------------- |
| **C** | Desde la declaración hacia los bloques anidados; ocultamiento si hay otra declaración con = nombre |
| **Pascal** | Contención de bloques (similar a C) |
| **ADA** | Desde donde se **declara hacia abajo** (no desde el inicio del bloque) |
| **Python** | La variable toma su valor del ámbito donde está **definida** la función, no de donde se la llama |

> Contraste: [[Alcance Dinámico]]
> Ver también: [[Atributo Alcance]], [[Variable]]
