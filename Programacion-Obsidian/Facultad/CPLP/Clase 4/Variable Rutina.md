---
aliases:
  - variable rutina
  - variables rutina
  - puntero a función
  - punteros a rutinas
---
Una **variable rutina** es una [[Variable]] cuyo valor es una referencia (puntero) a una [[Rutina]]. Permite una política **dinámica** de invocación: la rutina a ejecutar se determina en **ejecución**, no en compilación.

#### Ejemplo en C
```c
int (*pf)(int, int);   // declaración de variable puntero a función
pf = &suma;            // asignación: pf apunta a la función suma
pf(3, 5);              // invocación dinámica
```

El binding del R-valor de la rutina es **dinámico** (a diferencia del caso estático donde la rutina se invoca directamente por nombre).

> Ver también: [[Rutina]], [[Puntero]], [[Ligadura]]
