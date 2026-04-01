---
aliases:
  - gramaticales
  - gramática
  - gramáticas
  - grammar
---
Una **gramática** es un conjunto de reglas finitas que define un conjunto infinito de posibles sentencias válidas en un [[Lenguaje de Programación|lenguaje]].

#### Definición formal (4-tupla)
Una gramática está formada por:

**G = (N, T, S, P)**

| Componente | Significado                                    |
| ---------- | ---------------------------------------------- |
| **N**      | Conjunto de símbolos **no terminales**          |
| **T**      | Conjunto de símbolos **terminales**             |
| **S**      | Símbolo **distinguido** (pertenece a N)         |
| **P**      | Conjunto de **producciones** (reglas)           |

#### Formas de definir la [[Sintaxis]]
- **Lenguaje natural** (ej: Fortran)
- [[Gramática Libre de Contexto|Gramáticas libres de contexto]]:
	- [[BNF]] (Backus Naur Form) — ej: Algol
	- [[EBNF]]
	- [[Diagramas Sintácticos]] — equivalentes a BNF pero más intuitivos

#### Subgramáticas
La filosofía de **composición** permite definir gramáticas complejas reutilizando subgramáticas. Por ejemplo, una gramática de expresiones (GE) puede definirse utilizando las subgramáticas de números (GN) y de identificadores (GI). Es la forma en que trabajan los compiladores.

#### Tipos de gramáticas
- [[Gramática Libre de Contexto]] (CFG)
- [[Gramática Sensible al Contexto]] (CSG)
- [[Gramática Ambigua]]

#### Conceptos relacionados
- [[Producción Recursiva|Producciones recursivas]]
- [[Árbol de Derivación]]
- [[Parsing]]
