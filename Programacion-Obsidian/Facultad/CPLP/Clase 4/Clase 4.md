# Semántica Operacional — Unidades de Programa

Los [[Lenguaje de Programación|lenguajes de programación]] permiten que un programa esté compuesto por **unidades**. Una unidad es una **acción abstracta** que en general se denomina [[Rutina|rutina]].

| Tipo | Retorno |
| ---- | ------- |
| **Procedimiento** | No retorna un valor |
| **Función** | Retorna un valor |

> Algunos lenguajes solo tienen **funciones** y simulan procedimientos con funciones que devuelven `void` o `None` (ej. C, C++, Python).

---

# [[Rutina|Rutinas]] como 5-Tupla

Las rutinas, al igual que las [[Variable|variables]], se describen con atributos: `<NOMBRE, ALCANCE, TIPO, L-VALOR, R-VALOR>`.

## Nombre

El **nombre** es el string de caracteres que se usa para **invocar** la rutina (identificador). Se introduce en su **declaración** y se usa para invocarla.

> La llamada debe estar dentro del [[Atributo Alcance|alcance]] del nombre de la rutina.

## Alcance

El **alcance** de una rutina es el rango de instrucciones donde se conoce su nombre. Se extiende desde el punto de declaración hasta algún constructor de cierre.

La **activación** (llamada o invocación) solo puede ocurrir dentro del alcance de la rutina.

#### Ejemplo en C
```c
void uno() { ... }
void dos() { uno(); }  // CORRECTO: uno está en el alcance de dos
// uno() NO puede invocar a dos(): dos no está en su alcance (ANSI C)
```

### [[Definición vs Declaración]]

Algunos lenguajes (C, C++, Ada) distinguen entre **definición** y **declaración** de rutinas:

| Concepto | Contenido | Propósito |
| -------- | --------- | --------- |
| **Declaración** (prototipo/encabezado) | Firma: nombre, tipo de retorno, parámetros | Informa al compilador sobre existencia y estructura |
| **Definición** | Declaración + cuerpo | Proporciona las instrucciones que se ejecutarán |

```c
int sum(int n);              // declaración (prototipo)

int sum(int n) {             // definición
    int i, s = 0;
    for (i = 1; i <= n; ++i)
        s += i;
    return s;
}
```

Los prototipos son fundamentales para la organización del código, permitiendo el uso de funciones en múltiples archivos (ej. archivos `.h`).

#### Rutinas mutuamente recursivas
La distinción entre declaración y definición permite manejar esquemas donde **dos rutinas se llaman entre sí**:

```c
int A(int x, int y);   // declaración adelantada de A

float B(int z) {        // definición de B
    int w, u;
    w = A(z, u);        // A es visible por la declaración
}

int A(int x, int y) {   // definición de A
    float t;
    t = B(x);           // B ya está definida arriba
}
```

> En Pascal se usa `forward` para lograr el mismo efecto.

#### Prototipo por defecto
En algunas implementaciones de C, si no se encuentra la declaración de una función, el compilador **asume un prototipo que devuelve enteros**. Da error cuando el tipo de retorno real no coincide con lo supuesto.

## Tipo

El encabezado de la rutina define el tipo de los parámetros y el tipo del valor de retorno.

### [[Signatura]]

La **signatura** especifica el tipo de una rutina. Una rutina `fun` con parámetros de tipo `T1, T2, ..., Tn` que devuelve un valor de tipo `R`:

```
fun: T1 × T2 × ... × Tn → R
```

Un llamado es correcto si está de acuerdo a la signatura de la rutina. La conformidad requiere la **correspondencia de tipos** entre parámetros formales y reales.

#### Ejemplo
```c
int sum(int n) { ... }
// Signatura: sum: enteros → enteros
```

## L-Valor y R-Valor

| Atributo | Descripción |
| -------- | ----------- |
| **L-valor** | Lugar de memoria donde se almacena el **cuerpo** de la rutina |
| **R-valor** | La llamada causa la ejecución del código (constituye su R-valor) |

#### Binding del R-valor
- **Estático:** el caso más usual (la rutina se define y se invoca directamente)
- **Dinámico:** [[Variable Rutina|variables de tipo rutina]], implementadas a través de **punteros a rutinas**

```c
int (*pf)(int, int);   // variable puntero a función
pf = &suma;            // asignación
pf(3, 5);              // invocación dinámica
```

> El uso de punteros a rutinas permite una **política dinámica de invocación**.

---

# Comunicación entre Rutinas

Las rutinas se comunican mediante:
- **Ambiente no local:** [[Variable|variables]] no locales accesibles según reglas de [[Atributo Alcance|alcance]]
- **[[Parámetro|Parámetros]]:** permiten diferentes datos en cada llamado, mejorando legibilidad y modificabilidad

| Tipo | Descripción |
| ---- | ----------- |
| **[[Parámetro Formal]]** | Los que aparecen en la **definición** de la rutina |
| **[[Parámetro Real]]** | Los que aparecen en la **invocación** de la rutina (dato o rutina) |

## [[Ligadura entre Parámetros|Ligadura entre Parámetros Formales y Reales]]

### Método posicional
Los parámetros reales `Ri` se ligan a los formales `Fi` **por posición** (de 1 a n). Deben conocerse las posiciones.

```
routine S(F1, F2, ..., Fn)    // definición
call S(R1, R2, ..., Rn)      // llamado
```

**Variante con valores por defecto:**
```cpp
int distancia(int a = 0, int b = 0);
distancia();       // (0, 0)
distancia(10);     // (10, 0)
distancia(0, 0);   // (0, 0)
distancia(10, 0);  // (10, 0)
```

### Método por nombre
Se ligan por el **nombre** del parámetro formal. Deben conocerse los nombres.

```ada
-- Ada: permite valor por defecto, método posicional y por nombre
procedure Ejem(A: T1; B: T2 := w; C: T3);

Ejem(x, y, z);              -- posicional
Ejem(x, C => z);            -- x posicional, B por defecto, C por nombre
Ejem(C => z, A => x, B => y); -- todos por nombre
```

---

# Representación en Ejecución

La definición de una rutina especifica un proceso de cómputo. Cuando se invoca, se ejecuta una **instancia** del proceso con los valores particulares de los parámetros.

## [[Instancia de Unidad]]

| Componente | Contenido | Almacenamiento |
| ---------- | --------- | -------------- |
| **[[Segmento de Código]]** | Instrucciones de la unidad (**contenido fijo**) | Memoria de instrucciones (**C**) |
| **[[Registro de Activación]]** | Datos locales de la unidad (**contenido cambiante**) | Memoria de datos (**D**) |

## Elementos en ejecución

- **Punto de retorno:** información cambiante que se guarda en el [[Registro de Activación]] de la unidad llamada
- **Ambiente de referencia:**
  - **Ambiente local:** variables locales ligadas a objetos en su registro de activación
  - **Ambiente no local:** variables no locales ligadas a objetos en registros de activación de otras unidades

---

# [[Procesador Abstracto]] — SimpleSEM

El procesador abstracto sirve para comprender qué efecto causan las instrucciones del lenguaje al ser ejecutadas (**semántica intuitiva**). Se describe la semántica traduciendo cada constructor del lenguaje en instrucciones equivalentes del procesador abstracto.

```
       ip
        ↓
┌─────────────────┐  ┌─────────────────┐
│ Segmento de     │  │ Registro de     │
│ Código          │  │ Activación      │
│                 │  │                 │
│ Memoria C       │  │ Memoria D       │
└─────────────────┘  └─────────────────┘
```

#### Componentes

| Componente | Descripción |
| ---------- | ----------- |
| **C(y)** | Valor almacenado en la y-ésima celda de memoria de código (comienza en 0) |
| **D(y)** | Valor almacenado en la y-ésima celda de memoria de datos (comienza en 0). `y` representa el L-valor, `D(y)` su R-valor |
| **ip** | Puntero a la instrucción que se está ejecutando (se inicializa en 0) |

#### Ciclo de ejecución
1. Obtener la instrucción actual `C[ip]`
2. Incrementar `ip`
3. Ejecutar la instrucción actual

### Instrucciones que acceden a D

| Instrucción | Descripción | Ejemplo |
| ----------- | ----------- | ------- |
| `set target, source` | Copia `source` en `target` | `set 10, D[20]` → copia valor de posición 20 a 10 |
| `read` | Lee un valor del exterior | `set 15, read` → almacena en posición 15 |
| `write` | Escribe un valor al exterior | `set write, D[50]` → muestra valor en posición 50 |
| Expresiones | Combinaciones | `set 99, D[15]+D[33]*D[4]` |

### Instrucciones que acceden a C

| Instrucción | Descripción | Ejemplo |
| ----------- | ----------- | ------- |
| `jump` | Bifurcación **incondicional** | `jump 47` → la próxima instrucción es C[47] |
| `jumpt` | Bifurcación **condicional** (salta si verdadero) | `jumpt 47, D[13]>D[8]` |

#### Direccionamiento indirecto
```
D[10] = 30, D[20] = 5
set D[10], D[20]    → en D[30] almacena 5
jump D[30]          → ip = D[30] = 5 → salta a posición 5 en C
```

---

# [[Estructura de Ejecución]]

## [[Estructura Estática]] (espacio fijo)

- El espacio necesario para la ejecución se deduce del código
- Todos los requerimientos de memoria se conocen **antes** de la ejecución
- La [[Alocación de Memoria|alocación]] se hace **estáticamente**
- **No puede haber recursión** (no se pueden mantener diferentes instancias)
- Lenguajes: versiones originales de **FORTRAN** y **COBOL**

## [[Estructura Basada en Pila]] (espacio predecible)

- Programas más potentes cuyos requerimientos de memoria no pueden calcularse en traducción
- La memoria es predecible y sigue una disciplina **last-in-first-out**
- Las variables se alocan **automáticamente** y se desalocan cuando la rutina termina
- Se utiliza una **estructura de pila** para modelizarlo
- Lenguaje representativo: **Algol-60**

## [[Estructura Dinámica]] (espacio impredecible)

- Uso de memoria **impredecible**
- Los datos se alocan dinámicamente **solo cuando se necesitan** durante la ejecución
- No pueden modelizarse con una pila
- El programador puede crear objetos en cualquier punto arbitrario
- Los datos se alocan en la zona de memoria **heap**

---

# Esquemas de Ejecución

## Caso C1: Lenguaje Estático Simple

Características:
- Sentencias simples, tipos simples (enteros, reales, arreglos, estructuras)
- Sin funciones, datos estáticos de tamaño fijo
- Un programa = una rutina `main()`
- En zona de datos: **solo datos locales**

#### Ejemplo: algoritmo de Euclides (MCD)

```c
main() {
    int i, j;
    get(i, j);
    while (i != j)
        if (i > j)
            i -= j;
        else
            j -= i;
    print(i);
}
```

**Zona de datos:**

| D | Contenido |
| - | --------- |
| 0 | celda para `i` |
| 1 | celda para `j` |

**Zona de código (SimpleSEM):**

| C | Instrucción |
| - | ----------- |
| 0 | `set 0, read` |
| 1 | `set 1, read` |
| 2 | `jumpt 8, D[0] = D[1]` |
| 3 | `jumpt 6, D[0] <= D[1]` |
| 4 | `set 0, D[0] - D[1]` |
| 5 | `jump 7` |
| 6 | `set 1, D[1] - D[0]` |
| 7 | `jump 2` |
| 8 | `set write, D[0]` |
| 9 | `halt` |

## Caso C2: C1 + Rutinas Internas

Características:
- Datos globales, declaraciones de rutinas, rutina principal
- En zona de datos: datos locales + **punto de retorno** + valor de retorno (en funciones)
- El tamaño de cada [[Registro de Activación|R.A.]] se determina en compilación
- Todos los R.A. se alocan **antes de la ejecución** (alocación estática)
- Rutinas **disjuntas** (no anidadas) y **no recursivas**

#### Ambiente de las rutinas
- Datos locales
- Datos globales

#### Mecanismo CALL-RETURN
Antes de saltar a una rutina se guarda el **punto de retorno** en el [[Registro de Activación]] de la rutina llamada. Al terminar la rutina, se usa ese punto para regresar.

```c
int i = 1, j = 2, k = 3;

alpha() {
    int i = 4, l = 5;
    i += k + l;
}

beta() {
    int k = 6;
    i = j + k;
    alpha();
}

main() {
    beta();
}
```

**Zona de datos (registros de activación alocados estáticamente):**

| D | Variable | R.A. |
| - | -------- | ---- |
| 0 | `i` | global |
| 1 | `j` | global |
| 2 | `k` | global |
| 3 | retorno | alpha |
| 4 | `i` | alpha |
| 5 | `l` | alpha |
| 6 | retorno | beta |
| 7 | `k` | beta |

## Caso C2': C2 con Rutinas Compiladas por Separado

Las unidades del programa se encuentran en **archivos separados**, compilados **por separado y en orden arbitrario**.

```c
// file 1
int i = 1, j = 2, k = 3;
extern beta();
main() { beta(); }

// file 2
extern int k;
alpha() { ... }

// file 3
extern int i, j;
extern alpha();
beta() { alpha(); }
```

#### Problema
Como cada unidad se compila por separado, el compilador **no puede**:
- Ligar variables locales a **direcciones absolutas**
- Ligar variables globales con sus desplazamientos en el R.A. global
- Ligar invocaciones a rutinas con la dirección de inicio de sus segmentos de código

#### Solución: [[Linkeditor]]
El **linkeditor** se encarga de:
- **Combinar** los módulos compilados
- **Asignar** los segmentos de código al almacenamiento en C
- **Asignar** los registros de activación dentro de D
- **Completar** toda la información faltante que el compilador no podía evaluar

> C2 y C2' **no difieren semánticamente** una vez que el linkeditor reúne todas las unidades compiladas separadamente.
