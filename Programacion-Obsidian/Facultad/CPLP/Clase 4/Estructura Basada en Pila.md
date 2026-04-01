---
aliases:
  - estructura basada en pila
  - basado en pila
  - stack-based
---
En la **estructura basada en pila**, la memoria sigue una disciplina **last-in-first-out** (LIFO). Las [[Variable|variables]] se alocan automáticamente al invocar una [[Rutina]] y se desalocan cuando la rutina termina.

#### Características
- El espacio se deduce del código pero los requerimientos no pueden calcularse completamente en traducción
- Permite programas más potentes (ej. **recursión**)
- Se utiliza una **estructura de pila** para modelizar los [[Registro de Activación|registros de activación]]
- Cada invocación crea una nueva [[Instancia de Unidad|instancia]] en el tope de la pila

#### Lenguaje representativo
**Algol-60** fue pionero en este modelo.

> Ver también: [[Estructura de Ejecución]], [[Estructura Estática]], [[Estructura Dinámica]]
