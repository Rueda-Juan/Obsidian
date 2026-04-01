---
aliases:
  - ligadura
  - binding
  - bindings
---
La **ligadura** (binding) es el momento en el que un atributo de una entidad se asocia con un valor determinado. Es un concepto central en la definición de la [[Semántica]] de los [[Lenguaje de Programación|lenguajes de programación]].

#### Diferencias entre lenguajes
- El número de **entidades**
- El número de **atributos** que se les pueden ligar
- El **[[Momento de Ligadura]]** (binding time)
- La **[[Estabilidad de Ligadura|estabilidad]]** de la ligadura

#### Tipos de ligadura

| Tipo | Se establece | ¿Se puede modificar? |
| ---- | ------------ | -------------------- |
| **Estática** | Antes de la ejecución | No |
| **Dinámica** | Durante la ejecución | Sí (según reglas del lenguaje) |

> **Excepción:** las constantes tienen binding en ejecución pero no pueden ser modificadas.

> Ver también: [[Momento de Ligadura]], [[Estabilidad de Ligadura]], [[Variable]]
