---
aliases:
  - procesador abstracto
  - SimpleSEM
  - simplesem
---
El **procesador abstracto SimpleSEM** es un modelo teórico utilizado para comprender qué efecto causan las instrucciones de un [[Lenguaje de Programación]] al ser ejecutadas (**semántica intuitiva**).

Se describe la [[Semántica Operacional|semántica]] de cada constructor del lenguaje traduciéndolo en instrucciones equivalentes del procesador abstracto.

#### Componentes

| Componente | Descripción |
| ---------- | ----------- |
| **C(y)** | Celda y-ésima de memoria de **código** (desde 0) |
| **D(y)** | Celda y-ésima de memoria de **datos** (desde 0). `y` = L-valor, `D(y)` = R-valor |
| **ip** | Puntero a la instrucción en ejecución (se inicializa en 0) |

#### Ciclo de ejecución
1. Obtener la instrucción actual `C[ip]`
2. Incrementar `ip`
3. Ejecutar la instrucción actual

#### Instrucciones sobre D (datos)

| Instrucción | Descripción |
| ----------- | ----------- |
| `set target, source` | Copia `source` en `target` |
| `set n, read` | Lee del exterior y almacena en D(n) |
| `set write, D[n]` | Escribe D(n) al exterior |

#### Instrucciones sobre C (código)

| Instrucción | Descripción |
| ----------- | ----------- |
| `jump n` | Bifurcación incondicional a C(n) |
| `jumpt n, condición` | Bifurcación condicional si la condición es verdadera |

#### Direccionamiento indirecto
`set D[10], D[20]` → en la posición que indica D(10) almacena el valor de D(20).

> Ver también: [[Registro de Activación]], [[Segmento de Código]], [[Estructura de Ejecución]]
