---
aliases:
  - ligadura entre parámetros
  - método posicional
  - método por nombre
---
La **ligadura entre parámetros** formales y reales define cómo se asocian los [[Parámetro Real|argumentos]] de una invocación con los [[Parámetro Formal|parámetros]] de la definición de una [[Rutina]].

## Método posicional
Los parámetros reales `Ri` se ligan a los formales `Fi` **por posición** (1 a 1).

```
routine S(F1, F2, ..., Fn)    // definición
call S(R1, R2, ..., Rn)      // invocación: R1→F1, R2→F2, ...
```

**Variante con valores por defecto (C++):**
```cpp
int distancia(int a = 0, int b = 0);
distancia();       // usa (0, 0)
distancia(10);     // usa (10, 0)
```

## Método por nombre
Se ligan explícitamente por el **nombre** del formal. Deben conocerse los nombres.

**Ejemplo en Ada:**
```ada
procedure Ejem(A: T1; B: T2 := w; C: T3);

Ejem(x, y, z);                -- posicional
Ejem(x, C => z);              -- x posicional, B default, C por nombre
Ejem(C => z, A => x, B => y); -- todos por nombre
```

> Ver también: [[Parámetro]], [[Parámetro Formal]], [[Parámetro Real]], [[Rutina]]
