---
aliases:
  - gramática libre de contexto
  - CFG
  - context-free grammar
  - libre de contexto
---
Una **gramática libre de contexto** (CFG, Context-Free Grammar) es aquella en la que **no se realiza un análisis de contexto** para validar las sentencias.

Describe la [[Sintaxis]] de la mayoría de los [[Lenguaje de Programación|lenguajes]] modernos como C, Java y Python.

#### Limitaciones
No puede verificar:
- si una variable fue **declarada** antes de usarse
- si los **tipos son compatibles**
- No considera lo que se define antes ni después

Estas verificaciones se delegan a la fase de **análisis semántico** del compilador.

> Contraste: [[Gramática Sensible al Contexto]]

> Ver también: [[Gramática]], [[Sintaxis]], [[Semántica]]
