---
aliases:
  - semántica estática
  - análisis estático
---
La **semántica estática** se refiere a las verificaciones de significado que se realizan **sin ejecutar** el programa (ej. durante la compilación). Se ubica entre el [[Análisis Sintáctico]] y la [[Semántica Dinámica]], pero más cercana a la [[Sintaxis]].

#### ¿Qué detecta?
- Errores de **compatibilidad de tipos**
- **Declaración duplicada** de variables
- **Variables no declaradas** antes de ser referenciadas

[[BNF]]/[[EBNF]] no sirven para estos casos: son [[Gramática Libre de Contexto|gramáticas libres de contexto]] que no tienen memoria del contexto.

#### Herramienta formal
La [[Gramática de Atributos]] (Knuth, 1968) extiende a las gramáticas libres de contexto para describir y comprobar la corrección de las reglas semánticas estáticas.

> Ver también: [[Semántica Dinámica]], [[Gramática de Atributos]], [[Análisis Semántico]]
