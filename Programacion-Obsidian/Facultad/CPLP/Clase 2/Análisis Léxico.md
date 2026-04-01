---
aliases:
  - análisis léxico
  - analizador léxico
  - scanner
  - Scanner
---
El **análisis léxico** (Scanner) es la primera fase de la [[Etapa de Análisis]] de un [[Compilación|compilador]]. Reconoce **lexemas** (cadenas de caracteres) para clasificarlos en **tokens** (categorías léxicas).

#### Funciones
- Identificar y clasificar: identificadores, números, operadores, delimitadores, símbolos especiales, [[Palabra Reservada|palabras clave y reservadas]], comentarios
- **Filtrar** comentarios y separadores (espacios en blanco, tabulaciones)
- Mantener y consultar la [[Tabla de Símbolos]]; insertar identificadores nuevos con una referencia
- **Generar errores** si la secuencia de caracteres no coincide con ninguna categoría léxica

#### Ejemplo

Código fuente: `x := a + b * 10;`

Secuencia de tokens: `(id,1) (asign,:=) (id,2) (op,+) (id,3) (op,*) (num,10) (punt,;)`

> Ver también: [[Análisis Sintáctico]], [[Análisis Semántico]], [[Tabla de Símbolos]]
