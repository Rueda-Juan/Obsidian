---
aliases:
  - TAD
  - tipo abstracto de datos
  - tipos abstractos de datos
---
Un **Tipo Abstracto de Datos** (TAD) es un tipo definido por el usuario que oculta los detalles de la representación interna (**ocultamiento**). Quien lo utiliza no necesita conocer cómo están implementadas las operaciones.

#### Características
- Se asigna un **nombre** que lo identifica
- Define un conjunto de **operaciones permitidas** (público)
- Oculta los **detalles de implementación** (privado)
- No hay [[Ligadura|ligadura]] por defecto; el programador debe especificar la representación y las operaciones

#### TAD comunes
Listas, colas, pilas, árboles, grafos.

#### Ejemplo en C++: pila de caracteres
```cpp
class stack_of_char {
    int size;           // privado
    char* top;
    char* s;
public:                 // público
    stack_of_char(int sz) { top = s = new char[size = sz]; }
    ~stack_of_char() { delete[] s; }
    void push(char c) { *top++ = c; }
    char pop() { return *--top; }
    int length() { return top - s; }
};
```

> Ver también: [[Atributo Tipo]], [[Clases de Tipo]], [[Variable]]
