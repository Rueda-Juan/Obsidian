---
aliases:
  - estabilidad de ligadura
  - estabilidad
---
La **estabilidad de ligadura** determina si una [[Ligadura]] puede ser **modificada** una vez establecida.

| Estabilidad | Comportamiento |
| ----------- | -------------- |
| **Estable (estática)** | No se puede modificar después de establecida |
| **Inestable (dinámica)** | Puede modificarse durante la ejecución según reglas del lenguaje |

#### Ejemplo
¿Se puede cambiar el tipo de una variable asignado en compilación durante el tiempo de ejecución? Depende del lenguaje:
- En **C, Pascal, Java:** no (ligadura estática y estable)
- En **Python, Ruby, JavaScript:** sí (ligadura dinámica e inestable)

> Ver también: [[Ligadura]], [[Momento de Ligadura]]
