---
aliases:
  - compilación
  - compilador
  - compiladores
---
La **compilación** es una técnica de procesamiento de [[Lenguaje de Programación|lenguajes]] en la cual un programa llamado **compilador** traduce **todo** el programa fuente a un equivalente en lenguaje de máquina **antes de la ejecución**.

Ejemplos de lenguajes compilados: Ada, C, C++, Fortran, Pascal.

#### Proceso
El compilador toma todo el programa en un lenguaje de alto nivel (lenguaje fuente) y lo traduce completo. Pasa por **todas las instrucciones** antes de la ejecución.

#### Resultado
- **Código objeto:** generalmente el ejecutable en lenguaje de máquina (`.exe`)
- **Código intermedio:** en lenguaje ensamblador (`.obj`)

#### Estructura del compilador

| Etapa | Fase | Dependencia |
| ----- | ---- | ----------- |
| [[Etapa de Análisis]] | [[Análisis Léxico]], [[Análisis Sintáctico]], [[Análisis Semántico]] | Del lenguaje |
| [[Etapa de Síntesis]] | [[Optimización de Código]], generación de código final | De la máquina |

#### Características principales
- El código generado se guarda y se puede reusar ya compilado
- El código fuente **no es público**
- **Más rápido** en ejecución (ya está en bajo nivel)
- Se pierde la referencia entre código fuente y objeto (difícil ubicar errores)
- El compilador no necesita estar en memoria durante la ejecución

> Contraste: [[Interpretación]]
> Ver también: [[Traducción Híbrida]], [[Etapa de Análisis]], [[Etapa de Síntesis]], [[Linkeditor]], [[Registro de Activación]]
