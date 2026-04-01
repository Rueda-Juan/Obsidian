# Semántica

La [[Semántica]] describe el significado de los símbolos, palabras y frases de un lenguaje, ya sea un lenguaje natural o un [[Lenguaje de Programación|lenguaje informático]]. Describe el significado de programas [[Sintaxis|sintácticamente]] válidos para un lenguaje determinado, dando así significado a las construcciones del lenguaje.

> La semántica **no es igual** en todos los lenguajes. Código similar en distintos lenguajes puede dar distintas soluciones o reportar errores. Una cosa es el formato escrito y otra qué significa y cómo se comporta.

#### Ejemplos de diferencias semánticas
- En **C** es obligatorio declarar variables y tipos. El alcance de una variable puede ser global (accesible desde distintas funciones).
- En **Python** es fuertemente tipado pero no requiere declarar el tipo. Cuando una variable recibe una asignación dentro de una función pasa a ser local, dejando de considerarse global aunque existiera en el ámbito exterior. Se debe usar `global` explícitamente para mantener la referencia global.

#### Errores semánticos en C
Existen características de la estructura de los lenguajes que son difíciles o imposibles de describir con [[BNF]]/[[EBNF]]. Por ejemplo, exigir que una variable esté declarada antes de ser utilizada implica recordar información previa del programa. Una gramática BNF puede reconocer una asignación válida pero no puede verificar si la variable ya fue declarada, por lo que estas verificaciones se delegan al **análisis semántico**.

## Tipos de Semántica

- [[Semántica Estática]] (antes de la ejecución)
- [[Semántica Dinámica]] (durante la ejecución)

---

# [[Semántica Estática]]

Se la llama así porque el análisis para el chequeo se hace **sin necesidad de ejecutar** el programa (ej. en compilación). No está relacionada con el significado de la ejecución, sino más con las **formas válidas** (cercana a la [[Sintaxis]]). Se ubica entre el análisis sintáctico y el análisis de semántica dinámica.

#### Problemas que detecta
- Errores de **compatibilidad de tipos**
- **Declaración duplicada** de variables
- **Variables no declaradas** antes de referenciarlas

[[BNF]]/[[EBNF]] no sirve para estos casos: son [[Gramática Libre de Contexto|gramáticas libres de contexto]] que no se basan en el significado sino en las formas válidas.

## [[Gramática de Atributos]]

Las gramáticas de atributos son un enfoque formal inventado por **Knuth en 1968** para describir la [[Sintaxis]] y la [[Semántica Estática]]. Extienden a las [[Gramática Libre de Contexto|gramáticas libres de contexto]] agregando **información adicional** para dar significado.

#### Funcionamiento
A las construcciones del lenguaje representadas por símbolos de la [[Gramática]] (terminales o no terminales) se les asocian **atributos** que permiten describir y calcular información semántica del programa.

Un atributo puede ser:
- Valor de una variable
- Tipo de una variable o expresión
- Ubicación que ocupa una variable en memoria

Los valores de los atributos se obtienen mediante **ecuaciones o reglas semánticas** asociadas a las producciones gramaticales.

#### Estructura tabular

| Columna | Contenido |
| ------- | --------- |
| **Regla gramatical** | Producción sintáctica (símil BNF) |
| **Reglas semánticas** | Ecuaciones para calcular atributos |

Cuando en el [[Árbol de Derivación|árbol]] aparece una producción se aplican automáticamente las ecuaciones asociadas. Las ecuaciones indican cómo **calcular** los atributos a partir de otros atributos.

#### Ejemplo: declaración de variables `int` y `float` en C

| Regla gramatical | Regla semántica |
| ---------------- | --------------- |
| `decl → tipo lista-var` | `lista-var.at = tipo.at` |
| `tipo → int` | `tipo.at = int` |
| `tipo → float` | `tipo.at = float` |
| `lista-var → id` | `id.at = lista-var.at` · `Añadetipo(id.entrada, lista-var.at)` |
| `lista-var₁ → id, lista-var₂` | `id.at = lista-var₁.at` · `Añadetipo(id.entrada, lista-var₁.at)` · `lista-var₂.at = lista-var₁.at` |

> `id.entrada` referencia a la entrada del identificador en la [[Tabla de Símbolos]]. `Añadetipo` agrega el tipo a la [[Tabla de Símbolos]].

#### [[Árbol Sintáctico Atribuido]]

Parte del [[Árbol de Derivación]] y de la [[Gramática de Atributos]] para verificar cumplimiento y detectar errores. Ejemplo para `float z, t`:

```
              decl
             /    \
          tipo    lista-var
        (at=float) (at=float)
          |        /    \
        float    id  ,  lista-var
               (at=float) (at=float)
               Añadetipo    |
               (z, float)   id
                          (at=float)
                          Añadetipo
                          (t, float)
```

#### Detección de errores mediante la gramática de atributos
De la ejecución de las ecuaciones se pueden:
- Ingresar símbolos y atributos a la [[Tabla de Símbolos]]
- Detectar **variables duplicadas**
- Controlar **tipo y variables de igual tipo**
- Controlar **combinaciones no permitidas** (reglas específicas del lenguaje)

---

# [[Semántica Dinámica]]

Es la que describe el significado de **ejecutar** las diferentes construcciones del lenguaje de programación. Su efecto se ve **durante la ejecución** del programa. Influirán la interacción con el usuario y los errores de programación.

> Los programas solo se pueden ejecutar si son correctos tanto en **[[Sintaxis]]** como en **[[Semántica Estática]]**.

#### Ejemplo en C
```c
int notas[10];
```
Un vector de 10 elementos consecutivos en memoria de tipo entero. ¿Qué pasa si se exceden los límites? El comportamiento ante el acceso fuera de rango es parte de la semántica dinámica.

#### Dificultad para describirla
- No existen herramientas estándar fáciles y claras como en el caso de la [[Sintaxis]] ([[Diagramas Sintácticos]] y [[BNF]])
- Es complejo describir la relación entre entrada y salida del programa
- Es complejo describir cómo se ejecutará en cierta plataforma

## Enfoques de la Semántica Dinámica

| Enfoque | Idea principal | Cómo describe el programa | Uso principal |
| ------- | ------------- | ------------------------- | ------------- |
| [[Semántica Operacional]] | Ejecución paso a paso | Estados de una máquina abstracta y transiciones | Especificar cómo se ejecuta un programa |
| [[Semántica Denotacional]] | Significado matemático | Asocia cada construcción con una función matemática | Modelos formales de lenguajes |
| [[Semántica Axiomática]] | Propiedades lógicas | Axiomas y reglas de inferencia | Verificación de programas |

> Se pueden usar combinados. No todos sirven para todos los tipos de lenguajes.

### [[Semántica Axiomática]]

Considera al programa como una **máquina de estados** donde cada instrucción provoca un cambio de estado. Se parte de un axioma (verdad) para verificar estados y condiciones a probar. Se desarrolló para probar la **corrección de los programas**.

#### Notación: precondición y postcondición
Cada sentencia `S` se precede y se continúa con una expresión lógica:
- **Precondición (P):** condiciones de estado previo
- **Postcondición (Q):** condiciones de estado posterior

```
{P} S {Q}
```

#### Ejemplos
```
Precondición:  { b ≠ 0 }
Sentencia:     r = a / b
Postcondición: { a = b*c + r  ∧  r < b }
```

```
Precondición:  { x = 5 }
Sentencia:     x = x + 1
Postcondición: { x = 6 }
```

### [[Semántica Denotacional]]

Se basa en **modelos matemáticos** y describe el significado de programas mediante **funciones** (generalmente recursivas). Es más precisa para obtener y verificar resultados, pero menos legible e intuitiva.

A cada construcción sintáctica le asocia una función que define su significado. Describe la dependencia funcional entre el resultado de la ejecución y sus datos de entrada.

#### Ejemplo: conversión binario a entero

Gramática del número binario:
```
<Nbin> ::= 0 | 1 | <Nbin> 0 | <Nbin> 1
```

Función semántica recursiva:
```
FNbin(0) = 0                    FNbin(<Nbin> 0) = 2 * FNbin(<Nbin>)
FNbin(1) = 1                    FNbin(<Nbin> 1) = 2 * FNbin(<Nbin>) + 1
```

Evaluación de `110`:
```
FNbin(<Nbin>0) = 2 * FNbin(<Nbin>1)
               = 2 * [2 * FNbin(1) + 1]
               = 2 * [2 * 1 + 1]
               = 2 * 3
               = 6
```

### [[Semántica Operacional]]

Define el significado de un programa describiendo cómo se **ejecuta paso a paso**. El comportamiento se explica mediante operaciones de un lenguaje más simple o de bajo nivel, ejecutadas sobre una **máquina abstracta**. El significado del programa es la **secuencia de cambios de estado** durante su ejecución.

Es un método **informal** ya que se basa en otro lenguaje de bajo nivel. Es uno de los más utilizados en los libros de texto. PL/I fue el primero en utilizarlo en su definición.

#### Ejemplo: `for` de Pascal expresado en máquina abstracta

| Pascal | Máquina abstracta |
| ------ | ------------------ |
| `for i := pri to ul do begin ... end` | `i := pri` / `lazo: if i > ul goto sal` / `...` / `i := i + 1` / `goto lazo` / `sal: ...` |

---

# Procesamiento de los Programas

## Traducción

Las computadoras ejecutan un **lenguaje de máquina** (0s y 1s). Los programas están escritos en lenguajes de más alto nivel.

#### Historia
1. Se programaba en **código de máquina** (0s y 1s) — muy complejo y con muchos errores
2. Se reemplazaron patrones de bits por **código nemotécnico** (abreviatura del propósito de la instrucción)
3. Surgió el **[[Lenguaje Ensamblador]]** (que usa esos códigos) y el **programa ensamblador** (que lo convierte a lenguaje de máquina)
4. Cada arquitectura o familia de procesadores tiene su propio set de instrucciones, lenguaje ensamblador y código nemotécnico
5. Los **lenguajes de alto nivel** surgieron como solución a la falta de portabilidad

#### ¿Cómo se ejecutan los programas de alto nivel?
Con **programas procesadores del lenguaje**:
- [[Interpretación]]
- [[Compilación]]
- Combinación de ambos ([[Traducción Híbrida]])

> ¡No es decisión del programador! Es decisión del **desarrollador del lenguaje**.

---

## [[Interpretación]]

Existe un programa llamado **Intérprete** que procesa el lenguaje interpretado **en el momento de ejecución**.

Ejemplos: Lisp, Smalltalk, Basic, Python, Ruby, PHP, Perl

#### Proceso por cada sentencia
1. **Leer** la próxima sentencia
2. **Analizar**
3. **Decodificar**
4. **Ejecutar**

> Solo pasa por ciertas instrucciones según la ejecución. Cada vez que se vuelve a ejecutar el programa se repite toda la secuencia.

#### Mecanismo interno
Por cada constructor del lenguaje hay un **subprograma en lenguaje de máquina** que ejecuta esa acción. La interpretación se realiza llamando a estos subprogramas en la secuencia adecuada.

```
Datos → [Intérprete] ← Programa → Resultados
         (lee, analiza, decodifica, ejecuta)
```

---

## [[Compilación]]

Existe un programa llamado **Compilador** que traduce a lenguaje de máquina **antes de la ejecución**.

Ejemplos: Ada, C, C++, Fortran, Pascal

#### Características
- Toma **todo** el programa fuente y lo traduce a un equivalente a lenguaje de máquina
- Pasa por **todas** las instrucciones antes de la ejecución
- El código generado se **guarda** y se puede reusar ya compilado

#### Resultado
```
Código fuente → [Compilador] → Código intermedio → Código objeto
```

Se puede generar:
- **Código objeto:** generalmente el ejecutable en lenguaje de máquina
- **Código de nivel intermedio:** en lenguaje ensamblador

---

## Comparación: [[Compilación]] vs [[Interpretación]]

### Por cómo se ejecuta

| Aspecto | Intérprete | Compilador |
| ------- | ---------- | ---------- |
| **Cuándo traduce** | Durante la ejecución | Antes de la ejecución |
| **Qué produce** | Resultado directo | Programa ejecutable equivalente |
| **Código fuente** | Público (se necesita siempre) | No público |
| **Programa traductor** | Siempre debe estar presente | Solo necesario para compilar |

### Por el orden de ejecución

| Intérprete | Compilador |
| ---------- | ---------- |
| Sigue el **orden lógico** de ejecución (no necesariamente recorre todo) | Sigue el **orden físico** de las sentencias (recorre todo) |

### Por el tiempo de ejecución

| Intérprete | Compilador |
| ---------- | ---------- |
| Por cada sentencia realiza el proceso de decodificación (lee, analiza, ejecuta) — es repetitivo | Pasa por todas las sentencias una sola vez |
| En procesos iterativos, la decodificación se repite tantas veces como sea requerido | No repite lazos, traduce todo de una sola vez |
| La velocidad de proceso se puede ver afectada | Genera código objeto ya depurado y compilado |

### Por la eficiencia posterior

| Intérprete | Compilador |
| ---------- | ---------- |
| **Más lento** en ejecución — se repite el proceso cada vez | **Más rápido** — ya está en lenguaje de bajo nivel, listo para ejecutar |
| Se necesita el intérprete instalado en la otra máquina | Ya compilado es más eficiente |

### Por el espacio ocupado

**Intérprete:** la memoria se ocupa con el programa fuente (en su forma original), la [[Tabla de Símbolos]], variables y estructuras dinámicas, y el intérprete con todos sus subprogramas.

**Compilador:** la memoria se utiliza para el programa compilado (código máquina), datos del programa durante ejecución y bibliotecas necesarias. El compilador **no necesita estar en memoria** durante la ejecución.

> No es correcto afirmar simplemente que "el intérprete ocupa menos" o "el compilado ocupa más". Depende del **tamaño del programa** y de la **forma en que el lenguaje está implementado**.

### Por la detección de errores

| Intérprete | Compilador |
| ---------- | ---------- |
| Las sentencias del código fuente se relacionan directamente con la ejecución → **fácil ubicar** el error | Se pierde la referencia entre código fuente y código objeto → **difícil ubicar** el error |
| Más fácil **corregirlos** | Se deben usar otras técnicas |

### Tabla resumen

| Aspecto | Interpretación | Compilación |
| ------- | -------------- | ----------- |
| Momento de traducción | Durante la ejecución | Antes de ejecutar |
| Unidad de ejecución | Sentencia por sentencia | Programa completo |
| Velocidad de ejecución | Más lenta | Más rápida |
| Detección de errores | Aparecen al ejecutar la sentencia | Muchos se detectan antes |
| Depuración | Más fácil (paso a paso) | Puede requerir recompilación |
| Uso de memoria | Intérprete + programa + datos | Ejecutable + datos |
| Portabilidad | Alta si existe intérprete | Requiere recompilar |
| Distribución | Se distribuye el código fuente | Se distribuye un ejecutable |

---

## [[Traducción Híbrida]]

Combinación de técnicas de traducción para sacar provecho de sus diferencias.

### Interpretación + Compilación
El **intérprete** se utiliza en la etapa de desarrollo para facilitar el diagnóstico y depuración de errores. Se **compila** el programa validado para generar un código objeto más eficiente.

Ejemplos: QuickBasic, Lisp, Scheme

### Compilación a código intermedio + Máquina Virtual
Se realiza una traducción inicial a un **código intermedio** independiente de la máquina, que luego se ejecuta en una **máquina virtual**. Esto permite generar programas **portables**.

Ejemplos:
- **Java:** el compilador genera *bytecode*, ejecutado por la [[JVM]] (Java Virtual Machine)
- **C#** y **VB.NET**
- **Python**

```
Código fuente → [Compilación] → Código intermedio → [Interpretación/JIT] → Código ejecutable
```

> **JIT** (Just-In-Time) compila a código de máquina y elimina código repetido para agilizar la ejecución.

---

# [[Compilador|Compiladores]] — Funcionamiento

Los compiladores traducen **todo el programa**, pudiendo generar un código ejecutable (`.exe`) o un código intermedio (`.obj`). La compilación puede realizarse en 1 o 2 etapas.

## Estructura del compilador

### 1. [[Etapa de Análisis]]
Trabaja sobre el **programa fuente**. Depende del lenguaje.

#### [[Análisis Léxico]] (Scanner)
- Reconoce **lexemas** (cadena de caracteres) para luego reconocer **tokens** (categorías léxicas)
- Utiliza **reglas léxicas** para reconocer los tokens válidos
- Identifica y clasifica: identificadores, números, operadores, delimitadores, símbolos especiales, palabras clave, [[Palabra Reservada|palabras reservadas]], comentarios
- Filtra comentarios y separadores (espacios en blanco, tabulaciones)
- Mantiene y consulta la [[Tabla de Símbolos]]; inserta identificadores nuevos con una referencia a la tabla
- Genera errores si la secuencia de caracteres no coincide con ninguna categoría léxica

**Ejemplo de salida del analizador léxico para `x := a + b * 10;`**

| Token | Lexema |
| ----- | ------ |
| `(id, 1)` | `x` |
| `(asign, :=)` | `:=` |
| `(id, 2)` | `a` |
| `(op, +)` | `+` |
| `(id, 3)` | `b` |
| `(op, *)` | `*` |
| `(num, 10)` | `10` |
| `(punt, ;)` | `;` |

La [[Tabla de Símbolos]] almacena: `1 → x`, `2 → a`, `3 → b`.

#### [[Análisis Sintáctico]] (Parser)
- Recibe los tokens generados por el [[Análisis Léxico|Scanner]]
- Analiza la estructura del programa (sentencias, expresiones, declaraciones)
- Verifica si la secuencia de tokens cumple la [[Gramática]] del lenguaje
- Detecta y reporta **errores sintácticos**
- Construye un [[Árbol de Derivación|árbol de análisis sintáctico]]; si no puede construirlo, se detecta un error
- Utiliza las gramáticas formales que describen la [[Sintaxis]] del lenguaje

#### [[Análisis Semántico]] (Semántica estática)
- Se ejecuta **después** del [[Análisis Léxico|Scanner]] y el [[Análisis Sintáctico|Parser]]
- Trabaja sobre las estructuras ya reconocidas por el Parser
- Verifica que el programa tenga **significado válido** según las reglas del lenguaje
- Agrega información semántica al programa (tipos, alcance, referencias)

Funciones principales:
- **Comprobación y control de tipos** (compatibilidad entre variables, expresiones y operaciones)
- **Gestión de la [[Tabla de Símbolos]]:** se agregan atributos como tipo (`int`, `float`), alcance (local, global), clase de identificador (variable, función, constante)
- **Verificación de nombres:** variables declaradas o no antes de usarse, control de duplicados
- **Aplicación de reglas semánticas** mediante [[Gramática de Atributos|gramáticas de atributos]] y [[Árbol Sintáctico Atribuido|árboles atribuidos]]
- Es **puente** entre la [[Etapa de Análisis]] y la [[Etapa de Síntesis]]

### 2. [[Etapa de Síntesis]]
Genera el **programa objeto**. Depende de la máquina.

#### Generación de Código Intermedio
- Traduce el programa fuente a una representación intermedia para una **máquina abstracta**
- Es **independiente** de la arquitectura del hardware
- Facilita la optimización y la posterior generación de código objeto

**Código de tres direcciones:** `x := y op z`
```
while (a > 0) and (b < (a*4 - 5))
    a := b*a - 10;

-- Código de 3 direcciones:
L1: if (a > 0) goto L2
    goto L3
L2: t1 := a * 4
    t2 := t1 - 5
    if (b < t2) goto L4
    goto L3
L4: t1 := b * a
    t2 := t1 - 10
    a := t2
    goto L1
L3: ...
```

#### [[Optimización de Código]]

| Técnica | Ejemplo |
| ------- | ------- |
| **Eliminación de expresiones constantes** | `x := 3 * 4` → `x := 12` |
| **Eliminación de código muerto** | `t1 := a * b` (nunca se usa) → se elimina |
| **Eliminación de subexpresiones comunes** | `t1 := a + b; t2 := a + b` → `t2 := t1` |
| **Propagación de copias** | `t1 := a; b := t1` → `b := a` |
| **Simplificación algebraica** | `x := y * 1` → `x := y` |
| **Eliminación de saltos innecesarios** | Simplificación del flujo de control |

La optimización no siempre se realiza; puede activarse mediante **opciones de compilación** (ej. `gcc -O2 programa.c`).

**Niveles de optimización en GCC:**

| Flag | Descripción |
| ---- | ----------- |
| `-O0` | Sin optimización (default), ideal para depuración |
| `-O1` | Optimización básica |
| `-O2` | Optimización estándar, recomendado para la mayoría |
| `-O3` | Optimización alta (inlining, vectorización) |
| `-Os` | Optimiza para tamaño |
| `-Ofast` | Ignora estándares estrictos |
| `-Og` | Optimización para depuración |

#### Generación de Código Final y Enlace
- Se traduce el código intermedio a **instrucciones máquina**
- El **linkeditor** combina todos los módulos objeto en un único programa ejecutable (módulos, funciones, librerías, subrutinas)
- El **loader** del sistema operativo carga el programa en memoria para su ejecución

## Diagrama del compilador

```
PROGRAMA FUENTE
       ↓
 Analizador Léxico (Scanner)
       ↓
 Analizador Sintáctico (Parser)
       ↓
 Analizador Semántica Estática
       ↓
 Generador Código Intermedio
       ↓
 Optimizador de Código Intermedio
       ↓
 Generador de Código Objeto
       ↓
 Optimizador de Código
       ↓
 Linkeditor
       ↓
 Loader
       ↓
 PROGRAMA OBJETO
```

---

# Próxima Clase

Semántica operacional. Ligadura. Descriptores. Momentos de ligadura. Estabilidad. Variables. Arquitectura Von Neumann. Atributos. Nombre: características. Alcance: visibilidad, reglas. Tipo: definición, clasificación. L-valor: tiempo de vida, alocación. R-valor: constantes, inicialización. Alias.
