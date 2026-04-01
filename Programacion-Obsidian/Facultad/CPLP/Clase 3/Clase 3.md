# Semántica Operacional — Entidades de los Programas

La [[Semántica Operacional]] permite describir el significado preciso de un programa y verificar el resultado final de su ejecución. Es fundamental para el diseño de [[Lenguaje de Programación|lenguajes de programación]], la verificación de programas y la comprensión de cómo se ejecutan a un nivel más bajo.

Los [[Lenguaje de Programación|lenguajes de programación]] (C, Pascal, ADA, Ruby, Python, etc.) trabajan con **entidades** que poseen **atributos**. La información de estos atributos se almacena en un repositorio llamado [[Descriptor]], que se va completando durante la compilación y la ejecución.

| Entidad | Atributos |
| ------- | --------- |
| **Variables** | Nombre, tipo, rango de valores, área de memoria |
| **Rutinas / subprogramas** | Nombre, parámetros formales y reales, convención de pasaje, área de memoria |
| **Sentencias** | Acción asociada |

---

# [[Ligadura]]

La **ligadura** (binding) es el momento en el que un atributo se asocia con un valor determinado. Es un concepto central en la definición de la semántica de los lenguajes de programación.

Los programas trabajan con entidades, las entidades tienen atributos, y estos atributos deben **establecerse** (tener un valor) antes de poder usar la entidad.

#### Ejemplo
```c
int a;
```
- Entidad: Variable
- Atributos ligados: nombre → `a`, tipo → `int` (entero), rango de valores y operaciones → determinado por el tipo

#### Diferencias entre lenguajes
- El **número de entidades**
- El **número de atributos** que se les pueden ligar
- El **[[Momento de Ligadura]]** (binding time)
- La **[[Estabilidad de Ligadura|estabilidad]]** de la ligadura (¿una vez establecida se puede modificar?)

## [[Momento de Ligadura]] y [[Estabilidad de Ligadura|Estabilidad]]

#### Ligadura estática
1. Se establece **antes** de la ejecución
2. **No** se puede modificar

#### Ligadura dinámica
1. Se establece **durante** la ejecución
2. **Sí** puede modificarse durante la ejecución (según reglas del lenguaje)

> **Excepción:** las constantes tienen binding en ejecución pero **no pueden ser modificadas** luego de establecido.

#### Momentos posibles de ligadura

| Momento | Tipo | Ejemplo en C |
| ------- | ---- | ------------ |
| **Definición del lenguaje** | Estático | Forma de las sentencias, estructura del programa, nombres de tipos predefinidos (`int`) |
| **Implementación del lenguaje** | Estático | Set de valores y representación numérica, operaciones del tipo |
| **Compilación / traducción** | Estático | Asignación del tipo a variables (`int a`) |
| **Ejecución** | Dinámico | Variables se enlazan con valores (`a = 10`) y con su lugar de almacenamiento |

---

# [[Variable]] — La 5-Tupla

Una variable es una **5-tupla** de atributos:

```
<NOMBRE, ALCANCE, TIPO, L-VALOR, R-VALOR>
```

Cada atributo define un aspecto de la variable que influye en cómo se comporta el programa.

```
VARIABLE ←→ NOMBRE
                    ←→ CELDA DE MEMORIA (dirección)
                    ←→ VALOR (representación codificada)
                    ←→ SENTENCIA DE ASIGNACIÓN (modificación destructiva)
```

---

## [[Atributo Nombre]]

El nombre es el string de caracteres que se usa para **referenciar** a la variable (identificador). Se introduce mediante una sentencia de declaración.

#### Aspectos de diseño

**Longitud máxima** (se define en la etapa de definición del lenguaje):

| Lenguaje | Longitud |
| -------- | -------- |
| Fortran | 6 caracteres |
| C | Depende del compilador (suele ser 32, se ignora el resto) |
| Python, Pascal, Java, ADA | Cualquier longitud |

**Caracteres aceptados (conectores):**

| Lenguaje | Reglas |
| -------- | ------ |
| Python, C, Pascal | `_` permitido en el nombre |
| Ruby | Solo minúsculas para variables locales; `$` para variables globales |

**Sensibilidad a mayúsculas:**
- **C, C++, Java, Python:** sensibles (`Sum ≠ sum ≠ SUM`)
- **Pascal:** no sensible

**[[Palabra Reservada]] vs palabra clave:**
- **Palabra clave:** tiene significado especial solo en contextos particulares, puede usarse como identificador en otros contextos
- **Palabra reservada:** no puede usarse como identificador (ej. en Java `const` y `goto` no tienen significado pero no pueden usarse como identificadores)

---

## [[Atributo Alcance]]

El **alcance** de una variable es el rango de instrucciones en el que es conocido su nombre (visibilidad). Fuera de ese alcance la variable es **invisible**.

### Reglas de ligadura del alcance

#### 1. [[Alcance Estático]] (alcance léxico)

Se define en términos de la **estructura léxica** del programa. Se puede determinar examinando el texto del programa sin necesidad de ejecutarlo.

> La mayoría de los lenguajes adoptan reglas de alcance estático.

Si una unidad necesita referenciar una variable no declarada localmente, debe buscarla siguiendo la **estructura del programa** hacia las unidades más externas donde está contenida.

#### 2. [[Alcance Dinámico]]

Se define en términos de la **ejecución** del programa. Cada declaración extiende su efecto sobre todas las instrucciones ejecutadas posteriormente, hasta que una nueva declaración con el mismo nombre sea encontrada durante la ejecución.

Si una unidad necesita referenciar una variable no local, debe buscarla hacia afuera siguiendo la ejecución, viendo **quién llamó** a la unidad.

> Usada por: APL, Lisp (original), Afnix, TCL, Perl, Snobol4.

### Ejemplo comparativo (C-like)

```c
int x;
{ /* bloque A */ int x; ... }
{ /* bloque B */ int x; ... }
{ /* bloque C */ x = ...; }
```

| Tipo de alcance | Si A llama a C | Si B llama a C |
| --------------- | -------------- | -------------- |
| **Dinámico** | Toma `x` de A (¿quién lo llamó?) | Toma `x` de B |
| **Estático** | Toma `x` del bloque principal (¿dónde está contenido?) | Toma `x` del bloque principal |

### Ejemplo Pascal-like

```
Alcance dinámico: z := a + 1 + b → a es de tres() (a=20), b es de uno() (b=20) → Z=41
Alcance estático: z := a + 1 + b → a es de Alcance (a=4), b es de uno() (b=20) → Z=25
```

### Reglas por lenguaje

**C:** el alcance se extiende desde la declaración hacia los bloques anidados, a menos que aparezca otra declaración con el mismo nombre.

**Pascal:** similar a C, el alcance se visualiza mediante la contención de bloques.

**ADA:** el alcance es estático pero **desde donde se declara hacia abajo** (no desde el inicio del bloque).

**Python:** el alcance es estático. Por más que una función se llame desde otra, la variable toma su valor del ámbito donde está **definida** la función.

> En Python no confundir alcance estático con **tipado dinámico** (el tipo se infiere del valor asignado) y **fuertemente tipado** (no permite operaciones entre tipos distintos sin conversión).

### Comparación

| Alcance estático | Alcance dinámico |
| ---------------- | ---------------- |
| Más utilizadas por los LP | Menos utilizadas |
| Legibilidad y claridad | Más fáciles de implementar |
| Se determina en el texto del programa | Se determina en el flujo de ejecución |
| C, Pascal, ADA, Python, Java | APL, Lisp original, TCL, Perl |

### [[Clasificación de Variables por Alcance]]

| Tipo | Descripción |
| ---- | ----------- |
| **Global** | Creadas en el programa principal |
| **Local** | Creadas dentro de una unidad (programa o subprograma) |
| **No local** | Utilizadas dentro de un subprograma pero creadas fuera de él |

---

## [[Atributo Tipo]]

El tipo de una variable especifica:
1. El **conjunto de valores posibles** que se pueden asociar
2. El **conjunto de operaciones permitidas** sobre ella (crear, acceder, modificar)

> Antes de referenciar una variable hay que ligarle el tipo. Una variable de un tipo dado es una **instancia** de ese tipo.

#### Importancia del tipo
- **Protege** a las variables de operaciones no permitidas
- Permite realizar **chequeo de tipos**
- Verifica el uso correcto de las variables
- Ayuda a la **detección temprana de errores** y a la **confiabilidad** del código

#### Reglas de tipo por lenguaje

**ADA:**
- Fuertemente tipado (no se pueden mezclar tipos diferentes)
- No aplica conversión implícita
- Sí permite conversión **explícita** entre tipos relacionados (`X := Float(Y)`)

**Python:**
- Fuertemente tipado (no permite operaciones entre tipos diferentes directamente)
- Conversión **implícita:** sí (promoción de tipo en operaciones aritméticas)
- Conversión **explícita:** sí (`int()`, `float()`, `str()`, `list()`)

### [[Clases de Tipo]]

#### Tipos predefinidos (por el lenguaje)
Son los tipos base descriptos en la definición del lenguaje (enteros, reales, flotantes, booleanos). Cada uno tiene valores y operaciones asociadas. Los valores se ligan en la implementación a la representación de máquina.

```
boolean → valores: true, false → operaciones: and, or, not
```

#### Tipos definidos por el usuario
Permiten al programador definir nuevos tipos a partir de tipos base y constructores predefinidos. La declaración establece el binding en tiempo de traducción y heredan las operaciones de la estructura de datos base.

```c
// C
typedef int TipoVectorEnteros[4];
TipoVectorEnteros numeroDeCoches;
```

```pascal
// Pascal
type t = array[1..10] of integer;
```

#### [[Tipo Abstracto de Datos]] (TAD)
- El usuario no necesita conocer los detalles de la representación interna (**ocultamiento**)
- Se asigna un nombre y un set de **operaciones** (rutinas)
- Las operaciones permitidas son **públicas**; la implementación interna es **privada**
- El programador debe especificar la representación y las operaciones
- TAD comunes: listas, colas, pilas, árboles, grafos

```cpp
// C++ — Pila de caracteres
class stack_of_char {
    int size;
    char* top;
    char* s;
public:
    stack_of_char(int sz) { top = s = new char[size = sz]; }
    ~stack_of_char() { delete[] s; }
    void push(char c) { *top++ = c; }
    char pop() { return *--top; }
    int length() { return top - s; }
};
```

### [[Momento de Ligadura Variable-Tipo]]

#### Estático (static typing)
La ligadura se especifica en la **declaración** y se liga en **compilación**. No puede cambiarse en ejecución.

Ejemplos: Pascal, C, C++, Java, Fortran, COBOL, Algol, Simula, ADA.

Ventajas:
- Variables automáticamente **protegidas** de operaciones ilegales
- El compilador detecta **violaciones de semántica estática**
- **Chequeo de tipos estático** → detección temprana de errores → mayor confiabilidad

**Formas de ligadura estática:**

| Forma | Descripción | Ejemplo |
| ----- | ----------- | ------- |
| **Explícita** | Sentencia de declaración | `int x, y;` `bool z;` |
| **Implícita** | Se deduce por reglas propias del lenguaje | Fortran 77: variables I-N son enteras, el resto reales |
| **Inferida** | Se deduce del valor asignado o sus componentes (en traducción) | `var sum = 0` → se infiere entero. Swift: `var nombre = "Pedro"` → string |

#### Dinámico (dynamic typing)
El tipo se liga a la variable en **ejecución** y puede modificarse con sentencias de asignación.

Problemas:
- Mayor costo de implementación (comprobación de tipos, mantenimiento de [[Descriptor|descriptores]], cambios de tamaño en memoria)
- Chequeo dinámico → menor legibilidad, más posibilidad de errores

> Los lenguajes **interpretados** en general adoptan ligadura dinámica de tipos: APL, Snobol, JavaScript, Python, Ruby.

---

## [[Atributo L-Valor]]

El **L-valor** es la **dirección del área de memoria** ligada a la variable durante la ejecución. Las instrucciones acceden a la variable por su L-valor.

### [[Tiempo de Vida]] (lifetime)

Es el tiempo en que la variable está **alocada en memoria** y en el cual el binding existe. Desde que se solicita hasta que se libera.

### Tipos de [[Alocación de Memoria]]

#### Estática
Se hace en **compilación** (zona de datos al cargar el programa). Perdura hasta el fin de la ejecución. Es sensible a la historia.

#### Dinámica
Se hace en **tiempo de ejecución**:
- **Automática:** cuando aparece una declaración de variable en la ejecución
- **Explícita:** requerida por el programador mediante un constructor (ej. punteros, `new`)

#### Persistente
Los objetos persisten **más allá de la ejecución** del programa. Su tiempo de vida no tiene relación con el tiempo de ejecución.

Ejemplos: archivos, bases de datos.

### Ejemplo en C: `extern` y `static`

```c
// File 1
int x;               // variable externa
int func1() {
    float z;          // variable interna
}
int main() { ... }

// File 2
extern int x;         // extiende el alcance de x de File 1 a File 2
int i;
float func2() {
    int x;            // oculta la x externa dentro de func2
    int z;
}
```

- `extern`: extiende el alcance de una variable externa a otro archivo
- `static int m`: tiempo de vida = todo el programa; alcance = solo la función donde está definida
- `static` fuera de función: alcance desde donde está hasta el final del archivo; **no se puede extender** con `extern`

---

## [[Atributo R-Valor]]

El **R-valor** es el **valor codificado** almacenado en la ubicación (L-valor) asociada a la variable. La codificación se interpreta de acuerdo con el tipo.

```
R-Valor: 01110011
→ como int: interpreta un número entero
→ como char: interpreta una cadena
```

#### Objeto = (L-valor, R-valor)
```
x := x + 1
↑       ↑
l-valor  r-valor
```
Se accede a la variable por el L-valor (ubicación) y se puede modificar el R-valor (valor).

### Ligadura de variable a valor

**Binding dinámico:** el R-valor puede cambiar durante la ejecución con una asignación.

```
b := a    → copia el r-valor de a en el l-valor de b (cambia el r-valor de b)
a := 17   → asigna un valor directamente
```

**Constante:** se congela el R-valor, no puede cambiarse.

#### Constantes por lenguaje

| Lenguaje | Momento de ligadura del valor de constante |
| -------- | ------------------------------------------ |
| **Pascal** | En **compilación** (la expresión debe evaluarse en compile time) |
| **C y ADA** | En **ejecución** (permite expresiones con otras variables, se liga cuando se crea la variable) |

```ada
-- ADA: permite primero asignar x y luego definir la constante
x := 4;
c : constant Integer := x;  -- binding en ejecución, NO da error
```

```c
// C: la ligadura del r-valor es en ejecución
const int c = x + 1;  // permitido
```

```pascal
// Pascal: ERROR — el binding del r-valor es en compilación
const c = x + 1;  // no puede obtener el valor de x hasta runtime
```

### Inicialización

¿Cuál es el R-valor luego de crearse una variable?

| Estrategia | Descripción |
| ---------- | ----------- |
| **Por defecto** | Enteros → 0, caracteres → blanco, funciones → void |
| **En la declaración** | C: `int i = 0, j = 1;` · ADA: `I, J : Integer := 0;` |
| **Ignorar el problema** | Toma lo que hay en memoria (cadena de bits); puede llevar a errores |

---

# [[Puntero|Punteros]] y Variables Anónimas

Algunos lenguajes permiten que variables **sin nombre** (anónimas) sean accedidas por el R-valor de otra variable. Ese R-valor se denomina **referencia o puntero**.

> El R-valor de una variable puntero es la **referencia al L-valor** de otra variable.

#### Ejemplo en Pascal
```pascal
type pi = ^integer;
var pxi : pi;
new(pxi);          // aloca memoria en el heap a una variable anónima
pxi^ := 0;         // asigna valor 0 a la variable referenciada
```

El operador de **desreferenciación** (`^`) se aplica a una variable puntero para obtener su R-valor (que es el L-valor del objeto referenciado).

#### Puntero a puntero
```pascal
type ppi = ^pi;
var ppxi : ppi;
new(ppxi);
ppxi^ := pxi;     // asigna la dirección de pxi
```

---

## [[Alias]]

Se produce cuando **variables distintas comparten un mismo objeto** en el mismo entorno de referencia. Sus caminos de acceso conducen al mismo objeto.

```c
int x = 5;
int *px = &x;
int *py = px;      // py también apunta a x
*px = 10;          // efecto colateral: x, *px y *py son todos 10
```

#### Ventajas
- Compartir objetos para mejorar la **eficiencia**

#### Desventajas
- Generan errores: el valor se puede modificar sin usar su nombre
- Programas difíciles de leer y depurar

> Se recomienda **no usar alias**.

---

## [[Sobrecarga]]

Un nombre está **sobrecargado** si en un momento referencia más de una entidad. Es la capacidad de algunos lenguajes de definir comportamientos personalizados para operadores, métodos o funciones según el contexto.

```c
int i, j, k;
float a, b, c;
i = j + k;    // + suma enteros
a = b + c;    // + suma flotantes
```

Los **tipos** de las variables y los **parámetros** de las funciones permiten desambiguar en compilación.

| Concepto | Relación |
| -------- | -------- |
| **Alias** | Distintos nombres → 1 entidad |
| **Sobrecarga** | 1 nombre → distintas entidades |

- Debe estar **permitido** por el lenguaje
- Debe haber **suficiente información** para establecer la ligadura unívocamente (ej. por tipo)
