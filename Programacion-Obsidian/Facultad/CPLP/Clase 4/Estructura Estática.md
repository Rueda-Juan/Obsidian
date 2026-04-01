---
aliases:
  - estructura estática
  - espacio fijo
---
En la **estructura estática** de ejecución, el espacio necesario se deduce del código y todos los requerimientos de memoria se conocen **antes de la ejecución**.

#### Características
- La [[Alocación de Memoria|alocación]] se hace **estáticamente** (en compilación)
- **No puede haber recursión** (no se pueden mantener diferentes instancias simultáneas)
- Cada [[Variable]] se liga a una dirección de memoria D antes de la ejecución
- El tamaño de cada [[Registro de Activación|R.A.]] se determina en compilación

#### Lenguajes
Versiones originales de **FORTRAN** y **COBOL**.

#### Casos
- **C1:** lenguaje estático simple (un solo `main`, sin rutinas)
- **C2:** con rutinas internas disjuntas, no recursivas

> Ver también: [[Estructura de Ejecución]], [[Estructura Basada en Pila]], [[Estructura Dinámica]]
