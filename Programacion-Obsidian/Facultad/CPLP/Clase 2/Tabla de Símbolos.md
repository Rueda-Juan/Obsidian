---
aliases:
  - tabla de símbolos
---
La **tabla de símbolos** es una estructura de datos utilizada por el [[Compilador|compilador]] durante las distintas fases de la [[Etapa de Análisis]] para almacenar información sobre los identificadores del programa.

#### ¿Qué almacena?
- **Nombre** del identificador (lexema)
- **Tipo** (int, float, etc.)
- **Alcance** (local, global)
- **Clase** (variable, función, constante)
- **Ubicación en memoria**

#### ¿Quién la gestiona?
- El [[Análisis Léxico|analizador léxico]] inserta identificadores nuevos y genera una referencia en el token
- El [[Análisis Semántico|analizador semántico]] completa los atributos (tipo, alcance, clase)
- La [[Gramática de Atributos]] utiliza la función `Añadetipo` para registrar tipos

#### Ejemplo

| ID | Lexema | Tipo |
| -- | ------ | ---- |
| 1 | `x` | int |
| 2 | `a` | float |
| 3 | `b` | float |

> Ver también: [[Análisis Léxico]], [[Análisis Semántico]], [[Gramática de Atributos]]
