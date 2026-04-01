---
aliases:
  - interpretación
  - intérprete
  - intérpretes
---
La **interpretación** es una técnica de procesamiento de [[Lenguaje de Programación|lenguajes]] en la cual un programa llamado **intérprete** procesa y ejecuta el código fuente **en el momento de ejecución**, sentencia por sentencia.

Ejemplos de lenguajes interpretados: Lisp, Smalltalk, Basic, Python, Ruby, PHP, Perl.

#### Proceso por cada sentencia
1. **Leer** la próxima sentencia
2. **Analizar** la sentencia
3. **Decodificar** la acción a ejecutar
4. **Ejecutar** la acción

#### Mecanismo interno
Por cada constructor del lenguaje hay un **subprograma en lenguaje de máquina** que ejecuta esa acción. La interpretación se realiza llamando a estos subprogramas en la secuencia adecuada.

#### Características principales
- Solo pasa por ciertas instrucciones según la ejecución (no necesariamente recorre todo el código)
- Sigue el **orden lógico** de ejecución
- En procesos iterativos, la decodificación se repite tantas veces como sea requerido
- Se necesita el intérprete instalado y el código fuente es **público**
- Más fácil **detectar y corregir errores** (ubicación directa en el fuente)
- Cada ejecución repite toda la secuencia de procesamiento

> Contraste: [[Compilación]]
> Ver también: [[Traducción Híbrida]]
