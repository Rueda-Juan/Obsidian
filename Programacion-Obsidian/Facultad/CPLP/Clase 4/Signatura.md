---
aliases:
  - signatura
  - firma
  - signature
---
La **signatura** especifica el tipo de una [[Rutina]]. Describe la correspondencia entre tipos de los parámetros de entrada y el tipo del valor de retorno.

#### Notación
Una rutina `fun` con parámetros de tipo `T1, T2, ..., Tn` que devuelve un valor de tipo `R`:

```
fun: T1 × T2 × ... × Tn → R
```

#### Ejemplo
```c
int sum(int n) { ... }
```
Signatura: `sum: enteros → enteros`

#### Conformidad
Un llamado a una rutina es correcto si está de acuerdo a su signatura. Requiere la **correspondencia de tipos** entre [[Parámetro Formal|parámetros formales]] y [[Parámetro Real|reales]].

> Ver también: [[Rutina]], [[Atributo Tipo]], [[Parámetro]]
