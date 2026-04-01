---
aliases:
  - semántica operacional
---
La **semántica operacional** es un enfoque **no formal** de la [[Semántica Dinámica]] que define el significado de un programa describiendo cómo se **ejecuta paso a paso**. El comportamiento se explica mediante operaciones de un lenguaje más simple o de bajo nivel, ejecutadas sobre una **máquina abstracta**.

El significado de un programa es la **secuencia de cambios de estado** que se producen durante su ejecución.

#### Características
- Es un método **informal** ya que se basa en otro lenguaje de bajo nivel y puede llevar a cometer errores
- Es uno de los más utilizados en los **libros de texto** para explicar el significado de los lenguajes
- **PL/I** fue el primero que lo utilizó en su definición

#### Ejemplo: `for` de Pascal en máquina abstracta

| Pascal | Máquina abstracta |
| ------ | ------------------ |
| `for i := pri to ul do begin ... end` | `i := pri` → `lazo: if i > ul goto sal` → `...` → `i := i + 1` → `goto lazo` → `sal: ...` |

#### Implementaciones
Java Virtual Machine, intérprete de Python, intérpretes de lenguajes educativos.

> Ver también: [[Semántica Axiomática]], [[Semántica Denotacional]], [[Semántica Dinámica]], [[Procesador Abstracto]], [[Variable]], [[Ligadura]]
