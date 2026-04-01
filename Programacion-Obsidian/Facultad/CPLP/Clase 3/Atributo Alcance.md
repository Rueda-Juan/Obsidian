---
aliases:
  - alcance
  - atributo alcance
  - scope
  - visibilidad
---
El **alcance** de una [[Variable]] es el rango de instrucciones en el que es conocido su nombre (visibilidad). Fuera de ese alcance la variable es **invisible**.

#### Reglas de ligadura del alcance
- [[Alcance Estático]] (léxico): se determina por la estructura del texto del programa
- [[Alcance Dinámico]]: se determina por el flujo de ejecución del programa

#### [[Clasificación de Variables por Alcance]]

| Tipo | Descripción |
| ---- | ----------- |
| **Global** | Creadas en el programa principal |
| **Local** | Creadas dentro de un subprograma |
| **No local** | Usadas en un subprograma pero creadas fuera de él |

#### Comparación

| Alcance estático | Alcance dinámico |
| ---------------- | ---------------- |
| Más utilizado | Menos utilizado |
| Mayor legibilidad | Más fácil de implementar |
| Se determina en el texto | Se determina en la ejecución |

> Ver también: [[Variable]], [[Alcance Estático]], [[Alcance Dinámico]], [[Atributo Nombre]]
