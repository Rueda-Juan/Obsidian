---
aliases:
  - optimización de código
  - optimización
---
La **optimización de código** es una fase opcional de la [[Etapa de Síntesis]] de un [[Compilación|compilador]] que mejora el programa para que sea más eficiente (más rápido o más pequeño).

#### Técnicas comunes

| Técnica | Ejemplo |
| ------- | ------- |
| Eliminación de expresiones constantes | `x := 3 * 4` → `x := 12` |
| Eliminación de código muerto | Código que nunca se ejecuta → se elimina |
| Eliminación de subexpresiones comunes | `t1 := a + b; t2 := a + b` → `t2 := t1` |
| Propagación de copias | `t1 := a; b := t1` → `b := a` |
| Simplificación algebraica | `x := y * 1` → `x := y` |
| Eliminación de saltos innecesarios | Simplificación del flujo de control |

#### Niveles en GCC (`gcc -O`)

| Flag | Descripción |
| ---- | ----------- |
| `-O0` | Sin optimización (default) |
| `-O1` | Optimización básica |
| `-O2` | Estándar, recomendado |
| `-O3` | Alta (inlining, vectorización) |
| `-Os` | Para tamaño |
| `-Ofast` | Ignora estándares estrictos |
| `-Og` | Para depuración |

> La optimización puede estar integrada en el compilador o existir como herramienta independiente.

> Ver también: [[Etapa de Síntesis]], [[Compilación]]
