---
aliases:
  - análisis sintáctico
  - analizador sintáctico
  - parser
  - Parser
---
El **análisis sintáctico** (Parser) es la segunda fase de la [[Etapa de Análisis]] de un [[Compilación|compilador]]. Recibe los tokens del [[Análisis Léxico|Scanner]] y verifica si la secuencia cumple la [[Gramática]] del lenguaje.

#### Funciones
- Analizar la **estructura** del programa (sentencias, expresiones, declaraciones)
- Verificar si la secuencia de tokens cumple la [[Gramática]] del lenguaje
- Detectar y reportar **errores sintácticos**
- Construir un [[Árbol de Derivación|árbol de análisis sintáctico]] según la gramática
- Si no puede construir el árbol, se detecta un **error sintáctico**

#### El [[Árbol de Derivación|árbol]] permite
- Representar la estructura jerárquica del programa
- Mostrar cómo la sentencia se deriva según la gramática del lenguaje
- Servir de entrada para el [[Análisis Semántico]]

> Ver también: [[Análisis Léxico]], [[Análisis Semántico]], [[Gramática]]
