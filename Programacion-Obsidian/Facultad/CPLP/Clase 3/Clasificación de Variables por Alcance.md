---
aliases:
  - clasificación de variables por alcance
  - variable global
  - variable local
  - variable no local
---
Las [[Variable|variables]] se clasifican según su [[Atributo Alcance|alcance]] en:

| Tipo | Descripción | Ejemplo |
| ---- | ----------- | ------- |
| **Global** | Creadas en el programa principal; accesibles desde todo el programa | `x` declarada en el bloque principal |
| **Local** | Creadas dentro de una unidad (programa o subprograma); accesibles solo allí | `x` declarada dentro de `func()` |
| **No local** | Usadas dentro de un subprograma pero **no creadas** en él; son externas | `x` usada en `dos()` pero declarada en `uno()` |

> Las reglas de cada lenguaje determinan cómo se resuelve la referencia a una variable no local (ver [[Alcance Estático]] y [[Alcance Dinámico]]).

> Ver también: [[Atributo Alcance]], [[Variable]]
