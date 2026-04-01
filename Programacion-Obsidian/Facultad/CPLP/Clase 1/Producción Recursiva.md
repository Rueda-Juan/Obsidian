---
aliases:
  - producción recursiva
  - producciones recursivas
  - recursión en gramáticas
---
Las **producciones recursivas** son las que hacen que el conjunto de sentencias descrito por una [[Gramática]] sea **infinito**.

> Cualquier gramática que tiene una producción recursiva describe un **lenguaje infinito**.

#### Ejemplo
Sin recursión habría que enumerar infinitas producciones:
```
<natural> ::= <digito> | <digito><digito> | <digito><digito><digito> | ...
```

Con recursión:
```
<natural> ::= <digito> | <digito> <natural>
<digito>  ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
```

#### Tipos de recursión

| Tipo                          | Descripción                                                                                   | Asociatividad     |
| ----------------------------- | --------------------------------------------------------------------------------------------- | ----------------- |
| **Recursiva por la izquierda** | El no terminal de la parte izquierda aparece al **comienzo** de la parte derecha               | Por la izquierda  |
| **Recursiva por la derecha**   | El no terminal de la parte izquierda aparece al **final** de la parte derecha                  | Por la derecha    |

> Ver también: [[Gramática]], [[BNF]], [[EBNF]]
