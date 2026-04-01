---
aliases:
  - BNF extendido
  - Extended Backus-Naur Form
---
**EBNF** (Extended Backus-Naur Form) es una extensión de [[BNF]] que simplifica la escritura de [[Gramática|gramáticas]].

Es una [[Gramática Libre de Contexto]]. Su principal ventaja es que **elimina la recursión** y la reemplaza por **reiteración**, haciendo las producciones más fáciles de entender.

#### Metasímbolos incorporados

| Símbolo | Significado                        |
| ------- | ---------------------------------- |
| `[ ]`   | Elemento optativo (puede o no estar) |
| `(\|)`  | Selección de una alternativa        |
| `{ }*`  | Repetición 0 o más veces           |
| `{ }+`  | Repetición 1 o más veces           |

#### Ejemplo comparativo: definición de enteros con signo

**En BNF (recursivo):**
```
<enterosig> ::= + <entero> | - <entero> | <entero>
<entero> ::= <digito> | <entero><digito>
```

**En EBNF (iterativo):**
```
<enterosig> ::= [(+|-)] <digito>{<digito>}*
```

La versión EBNF eliminó la recursión y es más fácil de leer.

> Ver también: [[BNF]], [[Diagramas Sintácticos]], [[Gramática]]
