---
aliases:
  - diagramas sintácticos
  - diagrama sintáctico
  - carta sintáctica
  - grafo sintáctico
  - Conway
---
Los **diagramas sintácticos** (también llamados diagramas de Conway) son una representación gráfica equivalente a [[BNF]] y [[EBNF]], pero más intuitiva.

#### Características
- Cada diagrama tiene una **entrada** y una **salida**; el camino determina el análisis
- Cada diagrama representa una **regla o producción** de la [[Gramática]]
- Para que una sentencia sea válida, debe existir un camino desde la entrada hasta la salida que la describa
- Se **visualiza y entiende mejor** que BNF o EBNF

#### Elementos gráficos
| Elemento      | Representación             |
| ------------- | -------------------------- |
| **Terminales**    | Círculos / óvalos          |
| **No terminales** | Rectángulos                |
| **Flujo**         | Flechas                    |
| **Repetición**    | Caminos de retorno (loops) |
| **Selección**     | Caminos alternativos       |

> Ver también: [[BNF]], [[EBNF]], [[Gramática]]
