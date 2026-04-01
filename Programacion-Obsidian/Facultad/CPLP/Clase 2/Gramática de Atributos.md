---
aliases:
  - gramática de atributos
  - gramáticas de atributos
  - GA
---
Las **gramáticas de atributos** son un enfoque formal inventado por **Knuth en 1968** para describir la [[Sintaxis]] y la [[Semántica Estática]]. Extienden a las [[Gramática Libre de Contexto|gramáticas libres de contexto]] agregando información adicional para dar significado.

#### Funcionamiento
A los símbolos de la [[Gramática]] (terminales y no terminales) se les asocian **atributos** que permiten describir y calcular información semántica:
- Valor de una variable
- Tipo de una variable o expresión
- Ubicación en memoria

Los valores de los atributos se obtienen mediante **ecuaciones o reglas semánticas** asociadas a las producciones gramaticales.

#### Estructura tabular

| Columna | Contenido |
| ------- | --------- |
| **Regla gramatical** | Producción sintáctica (símil [[BNF]]) |
| **Reglas semánticas** | Ecuaciones para calcular atributos |

Cuando en el [[Árbol de Derivación|árbol]] aparece una producción se aplican automáticamente las ecuaciones asociadas.

#### Ejemplo: declaración `int` y `float` en C

| Regla gramatical | Regla semántica |
| ---------------- | --------------- |
| `decl → tipo lista-var` | `lista-var.at = tipo.at` |
| `tipo → int` | `tipo.at = int` |
| `tipo → float` | `tipo.at = float` |
| `lista-var → id` | `id.at = lista-var.at` · `Añadetipo(id.entrada, lista-var.at)` |
| `lista-var₁ → id, lista-var₂` | `id.at = lista-var₁.at` · `Añadetipo(id.entrada, lista-var₁.at)` · `lista-var₂.at = lista-var₁.at` |

#### Capacidades de detección
- Ingresar símbolos y atributos a la [[Tabla de Símbolos]]
- Detectar variables duplicadas
- Controlar tipos y combinaciones no permitidas

> Ver también: [[Semántica Estática]], [[Árbol Sintáctico Atribuido]], [[Tabla de Símbolos]]
