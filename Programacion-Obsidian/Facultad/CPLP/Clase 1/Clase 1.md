# Introducción

Un [[Lenguaje de Programación]] es un lenguaje formal diseñado para expresar algoritmos y describir procesos computacionales que pueden ser ejecutados por una máquina. Proporciona un conjunto de reglas sintácticas y semánticas que permiten especificar instrucciones que serán interpretadas o compiladas en operaciones ejecutables por un sistema informático.

Un lenguaje de programación puede seguir o respetar uno o varios [[Paradigma|paradigmas de programación]], que guían y dictan cómo se escriben y conceptualizan los programas.

> *"El valor de un lenguaje se debe juzgar según la forma en que afecta la producción de Software y a la facilidad con la que puede integrarse a otras herramientas"*

## Principales componentes de un Lenguaje de Programación
- [[Sintaxis]]
- [[Semántica]]
- [[Sistema de Tipos]]
- [[Modelo de Ejecución]]
- [[Mecanismos de Abstracción]]

## Objetivos de la materia
- Adquirir habilidad para **comprender y evaluar** lenguajes, identificando los conceptos más importantes, sus límites y posibilidades
- Habilidad para **elegir, diseñar, implementar o utilizar** un lenguaje de programación
- Enfatizar la **[[Abstracción]]** como la mejor forma de manejar la complejidad

## Estudio de conceptos de Lenguajes de Programación
- Aumentar la capacidad para **producir software**
- **Mejorar** el uso del lenguaje
- **Elegir mejor** un lenguaje
- Facilitar el **aprendizaje** de nuevos lenguajes
- Facilitar el **diseño e implementación** de lenguajes

---

# Criterios de Evaluación

Criterios para analizar la calidad del diseño de un [[Lenguaje de Programación]]:
- [[#Simplicidad y Legibilidad]]
- [[#Claridad en los Bindings]]
- [[#Confiabilidad]]
- [[#Soporte]]
- [[Abstracción]]
- [[Ortogonal|Ortogonalidad]]
- [[#Eficiencia]]

# Simplicidad y Legibilidad
#### Los [[Lenguaje de Programación|lenguajes de programación]] simples y legibles:
- producen programas fáciles de escribir y de leer. 
- fáciles a la hora de aprenderlo o enseñarlo 
- con sintaxis clara y pocas reglas complejas 
- evitan ambigüedades 

#### Permiten: 
- **en escritura (writability):** expresividad, rapidez al programar 
- **en legibilidad (readability):** favorece el mantenimiento del software, trabajo en equipo y revisión de código

#### Ejemplo de cuestiones que atentan contra esto:
- muchas componentes elementales, operadores sobrecargados 
- el mismo concepto semántico – distinta sintaxis 
- distintos conceptos semánticos - la misma notación sintáctica

# Claridad en los Bindings
Es la **asociación entre un nombre y una entidad del programa.** 

#### Ejemplos de bindings:
- nombre de variable y su valor 
- nombre de función y su implementación

#### La claridad en los bindings implica:
- saber cuándo y hasta cuándo ocurre la asociación 
- reglas de scope (alcance) claras y no ambiguas

#### Momentos posibles: 
- definición del [[Lenguaje de Programación|lenguaje]] 
- implementación del [[Lenguaje de Programación|lenguaje]] 
- en escritura del programa 
- compilación 
- cargado del programa 
- en ejecución

#### Tipos de binding: 
- **estático** (en compilación) 
- **dinámico** (en ejecución)

# Confiabilidad
La confiabilidad está relacionada con la seguridad. 
#### Un [[Lenguaje de Programación|lenguaje]] es confiable cuando: 
- evita errores comunes 
- ofrece **tipado fuerte**
- **detecta errores en compilación** 
- **previene** comportamientos inesperados 

#### Implica 
- **Chequeo de tipos:** Cuanto antes se encuentren errores menos costoso resulta realizar los arreglos que se requieran. 
- **Manejo de excepciones:** La habilidad para interceptar errores en tiempo de ejecución, tomar medidas correctivas y continuar.

# Soporte

#### un [[Lenguaje de Programación|lenguaje]] con un buen soporte facilita:
- el aprendizaje 
- el desarrollo 
- el mantenimiento

#### El soporte puede consistir en: 
- compiladores e intérpretes 
- bibliotecas 
- frameworks 
- herramientas de depuración 
- comunidad de desarrolladores 
- documentación 
- tutoriales

# [[Abstracción]]

# [[Ortogonal|Ortogonalidad]]

# Eficiencia

La **eficiencia** hace referencia al **uso eficiente de los recursos** computacionales por parte del programa generado por el lenguaje de programación. 
#### Afecta cuestiones como: 
- tiempo y espacio 
- esfuerzo humano 
- optimización 

#### Puede medirse: 
- tiempo de ejecución 
- uso de memoria 
- consumo de CPU

---

# [[Sintaxis]] y [[Semántica]]

Un [[Lenguaje de Programación]] ofrece una notación formal para describir algoritmos a ser ejecutados en una computadora. Requiere de una **[[Sintaxis]]** (si es válido el programa) y **[[Semántica]]** (qué significa) tanto para la programación como para su traducción.

- **Sintaxis:** conjunto de reglas que definen cómo componer letras, dígitos y otros caracteres para formar los programas
- **Semántica:** conjunto de reglas para dar significado a los programas sintácticamente válidos

## Elementos de la Sintaxis
- **Alfabeto o conjunto de caracteres:** con qué conjunto de caracteres se trabaja; la secuencia de bits que compone cada carácter determina la implementación
- **Identificadores:** por ejemplo conformados por letras y dígitos, que deben comenzar con una letra. Si se restringe la longitud se pierde legibilidad
- **Operadores:** 
	- *Uniformes:* la mayoría de los lenguajes usan `+`, `-` para suma y resta
	- *Poco uniformes:* para otros operadores no hay tanta uniformidad (`**`, `^`)
- **[[Palabra Reservada|Palabras clave y reservadas]]**
- **Comentarios:** para hacer los programas más legibles

> *"El código es leído muchas más veces de lo que es escrito"* — Guido Van Rossum (creador de Python)

## Estructura Sintáctica

**Vocabulario o words:** conjunto de caracteres y palabras necesarias para construir expresiones, sentencias y programas. Las words no son elementales, se construyen a partir del alfabeto.

**Expresiones:** funciones que a partir de un conjunto de datos devuelven un resultado. Son bloques sintácticos básicos a partir de los cuales se construyen las sentencias y programas.

**Sentencias:** componente sintáctico más importante. Tiene un fuerte impacto en la facilidad de escritura y legibilidad.

## Reglas Léxicas y Sintácticas

| Tipo                   | Descripción                                                     | Ejemplo                              |
| ---------------------- | --------------------------------------------------------------- | ------------------------------------ |
| **Reglas léxicas**     | Cómo formar las "words" a partir de los caracteres del alfabeto | `!=` vs `<>` para "distinto"         |
| **Reglas sintácticas** | Cómo son las sentencias y expresiones                           | En C el `if` no lleva `then`, en Pascal sí |

## Tipos de Sintaxis

| Tipo           | Se refiere a                  |
| -------------- | ----------------------------- |
| **Abstracta**  | La **estructura**             |
| **Concreta**   | La parte **léxica**           |
| **Pragmática** | El **uso práctico**           |

#### Ejemplo de sintaxis concreta y abstracta

```c
// En C
while (x != y) {
    // ...
}
```
```pascal
// En Pascal
while x <> y do begin
    // ...
end
```

- Son **diferentes** en sintaxis **concreta** (distinto símbolo de distinto, forma de encerrar bloques, uso de paréntesis)
- Son **iguales** en sintaxis **abstracta** (misma estructura: `while condición bloque`)

#### Ejemplo de sintaxis pragmática
- `<>` es más legible que `!=`
- En C y Pascal, `{}` o `begin-end` pueden omitirse si el bloque tiene una sola sentencia, lo que pragmáticamente puede conducir a error si luego se necesita agregar una sentencia

## Definición de la Sintaxis  
Se necesita una **descripción finita** para definir un conjunto infinito (el conjunto de todos los programas bien escritos).

Formas para definir la sintaxis:
- **Lenguaje natural** (ej: Fortran)
- **[[Gramática Libre de Contexto|Gramáticas libres de contexto]]:**
	- [[BNF]] (Backus Naur Form) — ej: Algol
	- [[EBNF]]
	- [[Diagramas Sintácticos]] — equivalentes a BNF pero más intuitivos

## [[Gramática]]

Una [[Gramatica|gramática]] es un conjunto de reglas finitas que define un conjunto infinito de posibles sentencias válidas en el lenguaje.

**G = (N, T, S, P)** donde N = no terminales, T = terminales, S = símbolo distinguido, P = producciones.

## [[Parsing]] y [[Árbol de Derivación|Árboles de Derivación]]

No todas las oraciones que se pueden armar con los terminales son válidas. Se necesita un método de análisis ([[Parsing]]) que permita determinar si un string es válido o no. El parser construye un **[[Árbol de Derivación]]** para cada sentencia.

## [[Producción Recursiva|Producciones Recursivas]]

Son las que hacen que el conjunto de sentencias descrito sea **infinito**. Cualquier gramática con una producción recursiva describe un lenguaje infinito.

- **Recursiva por la izquierda** → asociatividad por la izquierda
- **Recursiva por la derecha** → asociatividad por la derecha

## [[Gramática Ambigua|Gramáticas Ambiguas]]

Una gramática es **ambigua** si una sentencia puede derivarse de más de una forma, generando distintos árboles de derivación.

## Subgramáticas

Para definir gramáticas complejas se pueden reutilizar subgramáticas. Por ejemplo, una gramática de expresiones (GE) se puede definir utilizando las subgramáticas de números (GN) y de identificadores (GI). La filosofía de composición es la forma en que trabajan los compiladores.

## [[Gramática Libre de Contexto]] y [[Gramática Sensible al Contexto]]

- **Libre de contexto (CFG):** no realiza análisis de contexto. Describe la sintaxis de C, Java, Python. No puede verificar si una variable fue declarada o si los tipos son compatibles.
- **Sensible al contexto (CSG):** considera el contexto del programa (ej: Algol 68). Se maneja en la fase del análisis semántico del compilador.

## [[EBNF]] (BNF Extendido)
- Es una [[Gramática Libre de Contexto]]
- Simplifica la escritura eliminando la recursión y reemplazándola por **reiteración**
- Metasímbolos: `[ ]` optativo, `(|)` alternativa, `{}*` repetición 0+, `{}+` repetición 1+

## [[Diagramas Sintácticos]] (Conway)
- Representación gráfica equivalente a BNF/EBNF pero más intuitiva
- Cada diagrama tiene entrada y salida; el camino determina el análisis
- Cada diagrama representa una regla de la [[Gramática]]
