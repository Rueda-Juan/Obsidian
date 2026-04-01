---
aliases:
  - puntero
  - punteros
  - referencia
  - referencias
---
Un **puntero** es una [[Variable]] cuyo [[Atributo R-Valor|R-valor]] almacena la **dirección de memoria** ([[Atributo L-Valor|L-valor]]) de otra variable. Permite acceder a **variables anónimas** (sin nombre) de forma indirecta.

#### Mecanismo
```
puntero "ap" (dirección 012345)
  R-valor = 136520 → L-valor de "dato"
```
La diferencia con una variable común está en el **contenido**: un puntero almacena una dirección, no un dato directo.

#### Ejemplo en Pascal
```pascal
type pi = ^integer;
var pxi : pi;
new(pxi);          // aloca memoria en el heap para variable anónima
pxi^ := 0;         // desreferenciación: asigna 0 al dato apuntado
```

El operador de **desreferenciación** (`^` en Pascal, `*` en C) obtiene el R-valor del puntero, que es el L-valor del objeto referenciado.

#### Puntero a puntero
```pascal
type ppi = ^pi;
var ppxi : ppi;
new(ppxi);
ppxi^ := pxi;     // asigna la dirección almacenada en pxi
```

> Los punteros pueden generar [[Alias|aliases]] cuando múltiples punteros apuntan al mismo objeto.

> Ver también: [[Variable]], [[Alias]], [[Atributo L-Valor]], [[Atributo R-Valor]]
