---
aliases:
  - árbol sintáctico
  - árboles sintácticos
  - árboles de derivación
  - árbol de derivación
---
Un **árbol de derivación** (o árbol sintáctico) es la estructura que el [[Parsing|parser]] construye para cada sentencia válida de un [[Lenguaje de Programación]].

Muestra cómo una sentencia se **deriva** a partir del símbolo distinguido de la [[Gramática]], aplicando las producciones.

#### Métodos de construcción

| Método          | Dirección              |
| --------------- | ---------------------- |
| **Top-down**    | De izquierda a derecha |
|                 | De derecha a izquierda |
| **Bottom-up**   | De izquierda a derecha |
|                 | De derecha a izquierda |

> Los compiladores utilizan el **parse canónico**, que es el **bottom-up de izquierda a derecha**.

#### Ejemplo top-down de izquierda a derecha
Dada la gramática:
```
<oración>   ::= <sujeto> <predicado>
<predicado> ::= <verbo> <art> <objeto>
<sujeto>    ::= Juan | María
<art>       ::= un | una
<objeto>    ::= mascota | perro | gato
```

Derivación de "Juan adopta un perro":
```
<oración>
=> Juan <predicado>
=> Juan <verbo> <art> <objeto>
=> Juan adopta <art> <objeto>
=> Juan adopta un <objeto>
=> Juan adopta un perro
```

> Ver también: [[Parsing]], [[Gramática]], [[Gramática Ambigua]]
