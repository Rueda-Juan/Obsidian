---
aliases:
  - momento de ligadura
  - binding time
---
El **momento de ligadura** (binding time) es el instante en el que un atributo se asocia con un valor determinado. Los atributos pueden ligarse en diferentes momentos del ciclo de vida de un programa.

#### Momentos posibles

| Momento | Tipo | Ejemplo |
| ------- | ---- | ------- |
| **Definición del lenguaje** | Estático | Forma de sentencias, tipos predefinidos (`int`) |
| **Implementación del lenguaje** | Estático | Set de valores, representación numérica, operaciones |
| **Compilación / traducción** | Estático | Asignación de tipo a variables (`int a`) |
| **Ejecución** | Dinámico | Variables se enlazan con valores y almacenamiento (`a = 10`) |

> Ver también: [[Ligadura]], [[Estabilidad de Ligadura]], [[Variable]]
