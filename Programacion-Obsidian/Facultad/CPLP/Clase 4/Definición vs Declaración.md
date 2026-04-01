---
aliases:
  - definición vs declaración
  - prototipo
  - prototipos
  - encabezado
---
Algunos lenguajes (C, C++, Ada) distinguen entre **definición** y **declaración** de [[Rutina|rutinas]].

#### Diferencias

| Concepto | Contenido | Propósito |
| -------- | --------- | --------- |
| **Declaración** (prototipo) | Firma: nombre, tipo de retorno, parámetros | Informa al compilador antes de usar la rutina |
| **Definición** | Declaración + cuerpo | Proporciona las instrucciones ejecutables |

#### Ejemplo en C
```c
int sum(int n);              // declaración (prototipo)

int sum(int n) {             // definición (declaración + cuerpo)
    int i, s = 0;
    for (i = 1; i <= n; ++i)
        s += i;
    return s;
}
```

#### Utilidad
- Los prototipos permiten usar funciones en **múltiples archivos** (archivos `.h`)
- Permite manejar **rutinas mutuamente recursivas** (una llama a la otra y viceversa)
- En Pascal se usa `forward`; en C/C++ se adelanta la declaración

#### Prototipo por defecto
En algunas implementaciones de C, si no se encuentra el prototipo, el compilador asume que la función devuelve `int`. Da error cuando el tipo real no coincide.

> Ver también: [[Rutina]], [[Signatura]], [[Linkeditor]]
