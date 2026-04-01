---
aliases:
  - clases de tipo
  - tipos predefinidos
  - tipos definidos por el usuario
---
Las **clases de tipo** clasifican los tipos de datos según quién los define.

## Tipos predefinidos (por el lenguaje)
Son los tipos base descriptos en la **definición del lenguaje**: enteros, reales, flotantes, booleanos. Cada uno tiene valores y operaciones asociadas. Los valores se ligan en la implementación a la representación de máquina.

```
boolean → valores: true, false → operaciones: and, or, not
```

## Tipos definidos por el usuario
Permiten al programador definir **nuevos tipos** a partir de tipos base y constructores predefinidos. La declaración establece el binding en tiempo de traducción.

```c
typedef int TipoVector[4];   // C
```
```pascal
type t = array[1..10] of integer;   // Pascal
```

## [[Tipo Abstracto de Datos]] (TAD)
El usuario no necesita conocer la implementación interna (**ocultamiento**). Define operaciones **públicas** y representación **privada**.

TAD comunes: listas, colas, pilas, árboles, grafos.

> Ver también: [[Atributo Tipo]], [[Variable]], [[Tipo Abstracto de Datos]]
