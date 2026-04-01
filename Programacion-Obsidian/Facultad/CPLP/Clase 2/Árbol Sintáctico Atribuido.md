---
aliases:
  - árbol sintáctico atribuido
  - árboles sintácticos atribuidos
  - árbol atribuido
---
Un **árbol sintáctico atribuido** es un [[Árbol de Derivación]] decorado con los valores de los atributos calculados a partir de una [[Gramática de Atributos]]. Permite verificar el cumplimiento de las reglas semánticas y **detectar errores** en tiempo de compilación.

#### Ejemplo: `float z, t`

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

Los atributos se propagan de arriba hacia abajo (del tipo a la lista de variables), y en cada `id` se ejecuta `Añadetipo` para registrar el símbolo en la [[Tabla de Símbolos]].

> Ver también: [[Gramática de Atributos]], [[Semántica Estática]], [[Análisis Semántico]]
