---
aliases:
  - etapa de síntesis
---
La **etapa de síntesis** es la segunda etapa de un [[Compilación|compilador]]. Genera el **programa objeto** y depende de la **máquina** (procesador, arquitectura).

#### Fases

| Orden | Fase | Función |
| ----- | ---- | ------- |
| 1 | Generación de código intermedio | Traduce a representación independiente de la arquitectura |
| 2 | [[Optimización de Código]] | Mejora la eficiencia (opcional) |
| 3 | Generación de código objeto | Traduce a instrucciones máquina |
| 4 | Linkeditor | Combina módulos objeto en un ejecutable |
| 5 | Loader | Carga el programa en memoria para ejecución |

#### Código de tres direcciones
Representación intermedia con instrucciones simples: `x := y op z`

Expresiones complejas se descomponen en pasos simples usando **variables temporales**.

> Ver también: [[Etapa de Análisis]], [[Compilación]], [[Optimización de Código]]
