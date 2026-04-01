---
aliases:
  - estructura de ejecución
  - esquema de ejecución
---
La **estructura de ejecución** define cómo se gestiona la memoria durante la ejecución de un programa. Determina cuándo y cómo se alocan/desalocan los [[Registro de Activación|registros de activación]].

#### Tipos

| Tipo | Espacio | Recursión | Lenguajes |
| ---- | ------- | --------- | --------- |
| **[[Estructura Estática\|Estático]]** | Fijo, deducible del código | No soporta | FORTRAN, COBOL (versiones originales) |
| **[[Estructura Basada en Pila\|Basado en pila]]** | Predecible (LIFO) | Sí soporta | Algol-60, C, Pascal |
| **[[Estructura Dinámica\|Dinámico]]** | Impredecible (heap) | Sí soporta | Lenguajes con objetos dinámicos |

> Ver también: [[Registro de Activación]], [[Rutina]], [[Alocación de Memoria]]
