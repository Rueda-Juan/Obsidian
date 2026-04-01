---
aliases:
  - semántica axiomática
---
La **semántica axiomática** es un enfoque formal de la [[Semántica Dinámica]] que considera al programa como una **máquina de estados** donde cada instrucción provoca un cambio de estado. Se desarrolló para probar la **corrección de los programas**.

La notación empleada es el **cálculo de predicados**, un lenguaje lógico que permite expresar propiedades matemáticas sobre variables y estados del programa.

#### Notación: precondición y postcondición
Cada sentencia `S` se describe con:
- **Precondición (P):** descripción del estado previo
- **Postcondición (Q):** descripción del estado posterior

```
{P} S {Q}
```

#### Ejemplos
```
{b ≠ 0}  r = a / b  {a = b*c + r  ∧  r < b}
{x = 5}  x = x + 1  {x = 6}
```

#### Herramientas
Coq, Isabelle, verificación en SPARK.

> Referencia: trabajos de C.A.R. Hoare.
> Ver también: [[Semántica Denotacional]], [[Semántica Operacional]], [[Semántica Dinámica]]
