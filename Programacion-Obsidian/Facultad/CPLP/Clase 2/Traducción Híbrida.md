---
aliases:
  - traducción híbrida
  - técnica híbrida
---
La **traducción híbrida** combina técnicas de [[Interpretación]] y [[Compilación]] para aprovechar las ventajas de ambas.

#### Interpretación + Compilación
Se usa el **intérprete** en la etapa de desarrollo para facilitar el diagnóstico y depuración de errores. Luego se **compila** el programa validado para generar un código objeto más eficiente.

Ejemplos: QuickBasic, Lisp, Scheme.

#### Compilación a código intermedio + Máquina Virtual
Se realiza una traducción inicial a un **código intermedio** independiente de la máquina, que luego se ejecuta en una **máquina virtual**. Esto genera programas **portables**.

Ejemplos:
- **Java:** bytecode ejecutado por la [[JVM]]
- **C#** y **VB.NET:** código intermedio (IL) ejecutado por el CLR
- **Python:** bytecode ejecutado por la Python VM

**JIT** (Just-In-Time) compila a código de máquina y elimina código repetido para agilizar.

> Ver también: [[Compilación]], [[Interpretación]], [[JVM]]
