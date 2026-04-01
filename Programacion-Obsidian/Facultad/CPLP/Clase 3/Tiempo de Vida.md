---
aliases:
  - tiempo de vida
  - lifetime
  - extensión
---
El **tiempo de vida** (lifetime) de una [[Variable]] es el periodo en que está **alocada en memoria** y en el cual el binding del [[Atributo L-Valor|L-valor]] existe. Es desde que se solicita la memoria hasta que se libera.

#### Relación con el L-valor
El tiempo de vida está directamente ligado al L-valor: la variable solo es accesible mientras su área de memoria esté reservada.

#### Múltiples alocaciones
En llamadas recursivas o invocaciones repetidas, una misma variable puede tener **múltiples alocaciones** en distintas zonas de memoria, cada una con su propio tiempo de vida.

#### Relación con el [[Atributo Alcance|alcance]]

| Caso | Descripción | Ejemplo en C |
| ---- | ----------- | ------------ |
| **Tiempo de vida > Alcance** | La variable existe en memoria pero su nombre no es visible | Variable `static` en una función: vive toda la ejecución pero solo se nombra dentro de la función |
| **Tiempo de vida < Alcance** | El nombre es visible pero la memoria ya no está reservada | [[Puntero]] a variable local de una función que ya retornó (dangling pointer) |
| **Tiempo de vida = Alcance** | La variable existe exactamente mientras su nombre es visible | Variable local automática en un bloque |

> Ver también: [[Atributo L-Valor]], [[Alocación de Memoria]], [[Variable]], [[Atributo Alcance]]
