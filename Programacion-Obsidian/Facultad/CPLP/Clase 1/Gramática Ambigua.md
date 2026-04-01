---
aliases:
  - gramática ambigua
  - gramáticas ambiguas
  - ambigüedad
---
Una [[Gramática]] es **ambigua** si una sentencia puede derivarse de **más de una forma**, generando distintos [[Árbol de Derivación|árboles de derivación]].

#### Ejemplo de gramática ambigua
```
G = (N, T, S, P)
N = { <id>, <exp>, <asig> }
T = { A, B, C, +, *, -, /, := }
S = <asig>

P = {
  <asig> ::= <id> := <exp>
  <exp>  ::= <exp>+<exp> | <exp>*<exp> | <exp>-<exp> | <exp>/<exp> | <id>
  <id>   ::= A | B | C
}
```

La expresión `A + B * C` puede derivarse de dos formas distintas (con distinta prioridad de operadores), lo que genera ambigüedad.

Para resolverla se deben agregar niveles de precedencia en las producciones.

> Ver también: [[Gramática]], [[Árbol de Derivación]], [[Parsing]]
