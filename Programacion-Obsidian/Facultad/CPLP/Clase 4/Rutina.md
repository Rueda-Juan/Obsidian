---
aliases:
  - rutina
  - rutinas
  - subprograma
  - subprogramas
---
Una **rutina** es una unidad de programa que representa una **acción abstracta**. Los [[Lenguaje de Programación|lenguajes de programación]] permiten que un programa esté compuesto por múltiples rutinas.

#### Tipos

| Tipo | Retorno |
| ---- | ------- |
| **Procedimiento** | No retorna un valor |
| **Función** | Retorna un valor |

> Algunos lenguajes solo tienen funciones y simulan procedimientos con `void`/`None` (C, C++, Python).

#### Atributos (5-Tupla)
Al igual que las [[Variable|variables]], las rutinas se describen con:

| Atributo | Descripción |
| -------- | ----------- |
| **Nombre** | Identificador para invocar la rutina |
| **[[Atributo Alcance\|Alcance]]** | Rango donde se conoce el nombre |
| **[[Signatura\|Tipo]]** | Tipos de parámetros y retorno |
| **L-valor** | Lugar de memoria del cuerpo |
| **R-valor** | La ejecución del código (estático o dinámico via [[Variable Rutina\|punteros a rutinas]]) |

> Ver también: [[Definición vs Declaración]], [[Signatura]], [[Parámetro]], [[Registro de Activación]]
