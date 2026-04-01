---
aliases:
  - linkeditor
  - linker
  - enlazador
---
El **linkeditor** (linker) es el programa encargado de combinar módulos compilados por separado y completar la información que el [[Compilación|compilador]] no pudo resolver.

#### Funciones
- **Combinar** los módulos compilados separadamente
- **Asignar** los [[Segmento de Código|segmentos de código]] al almacenamiento en la memoria C
- **Asignar** los [[Registro de Activación|registros de activación]] dentro de la memoria D
- **Completar** información faltante:
  - Direcciones absolutas de variables locales
  - Desplazamientos de variables globales en el R.A. global
  - Direcciones de inicio de los segmentos de código de las rutinas

#### ¿Por qué es necesario?
Cuando cada unidad de un programa se compila **por separado y en orden arbitrario**, el compilador no puede ligar variables a direcciones absolutas ni invocaciones a direcciones de código. El linkeditor resuelve estas referencias cruzadas.

> Ver también: [[Compilación]], [[Registro de Activación]], [[Segmento de Código]], [[Etapa de Síntesis]]
