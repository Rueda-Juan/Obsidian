---
aliases:
  - variable
  - variables
---
Una **variable** es una abstracción de una celda de memoria. Se define como una **5-tupla** de atributos:

```
<NOMBRE, ALCANCE, TIPO, L-VALOR, R-VALOR>
```

| Atributo | Descripción |
| -------- | ----------- |
| [[Atributo Nombre\|Nombre]] | String de caracteres que referencia a la variable (identificador) |
| [[Atributo Alcance\|Alcance]] | Rango de instrucciones donde es visible |
| [[Atributo Tipo\|Tipo]] | Conjunto de valores posibles y operaciones permitidas |
| [[Atributo L-Valor\|L-valor]] | Dirección del área de memoria asociada |
| [[Atributo R-Valor\|R-valor]] | Valor codificado almacenado en la ubicación |

#### Conceptos asociados
- La sentencia de **asignación** produce la **modificación destructiva** del R-valor en la celda
- Un **objeto** se define como el par `(l-valor, r-valor)` → `(dirección, valor)`

> Ver también: [[Ligadura]], [[Descriptor]], [[Puntero|Punteros]]
