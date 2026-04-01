---
aliases:
  - Backus Naur Form
  - Backus-Naur Form
---
**BNF** (Backus Naur Form) es una notación formal para describir la [[Sintaxis]] de un [[Lenguaje de Programación]].

Es un **metalenguaje** que utiliza **metasímbolos** para definir reglas de producción.

#### Metasímbolos
| Símbolo | Significado |
| ------- | ---------------------- |
| `< >`   | No terminal            |
| `::=`   | Se define como         |
| `\|`    | Alternativa (o)        |

#### Ejemplo
```
<digito> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
```
- `<digito>` es un **no terminal**
- `0`, `1`, ..., `9` son **terminales**
- `::=` significa "se define como"

> Ver también: [[EBNF]], [[Gramática]], [[Diagramas Sintácticos]]
