---
aliases:
  - lenguaje ensamblador
  - ensamblador
  - assembly
---
El **lenguaje ensamblador** es un lenguaje de bajo nivel que reemplaza patrones de bits por **código nemotécnico** (abreviaturas del propósito de la instrucción). Un **programa ensamblador** lo convierte a lenguaje de máquina.

#### Características
- Cada arquitectura o familia de procesadores tiene su **propio** lenguaje ensamblador
- Diferentes versiones de una CPU pueden tener juegos de instrucciones **incompatibles**
- Modelos evolucionados pueden incorporar instrucciones nuevas
- Es imposible intercambiar programas entre distintas máquinas directamente

#### Ejemplo
```asm
SUM #10, #11, #13
SUM #13, #12, #13
DIV #13, 3, #13
FIN
```

Los **lenguajes de alto nivel** surgieron como solución a estas limitaciones de portabilidad.

> Ver también: [[Compilación]], [[Interpretación]]
