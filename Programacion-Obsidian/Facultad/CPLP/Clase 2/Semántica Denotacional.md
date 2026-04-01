---
aliases:
  - semántica denotacional
---
La **semántica denotacional** es un enfoque formal de la [[Semántica Dinámica]] que se basa en **modelos matemáticos** y describe el significado de programas mediante **funciones** (generalmente recursivas). Es más precisa para obtener y verificar resultados, pero menos legible e intuitiva.

A cada construcción sintáctica le asocia una **función que define su significado**. Describe la dependencia funcional entre el resultado de la ejecución y sus datos de entrada.

#### Diferencia con la [[Semántica Axiomática]]
- **Axiomática:** describe el significado a través de **predicados** (sobre estados del programa)
- **Denotacional:** describe el significado a través de **funciones** (generalmente recursivas) que definen el significado matemático

#### Ejemplo: conversión binario a entero
Gramática: `<Nbin> ::= 0 | 1 | <Nbin> 0 | <Nbin> 1`

Función semántica recursiva:
```
FNbin(0) = 0                    FNbin(<Nbin> 0) = 2 * FNbin(<Nbin>)
FNbin(1) = 1                    FNbin(<Nbin> 1) = 2 * FNbin(<Nbin>) + 1
```

Evaluación de `110` → `FNbin = 6`

#### Herramientas
K Framework, diseño de lenguajes funcionales como Haskell.

> Referencia: trabajos de Dana Scott.
> Ver también: [[Semántica Axiomática]], [[Semántica Operacional]], [[Semántica Dinámica]]
