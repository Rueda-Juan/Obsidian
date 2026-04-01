---
aliases:
  - sobrecarga
  - overloading
---
La **sobrecarga** es una característica de algunos [[Lenguaje de Programación|lenguajes de programación]] que permite definir comportamientos personalizados para operadores, métodos o funciones. Un nombre está sobrecargado si en un momento referencia **más de una entidad**.

#### Requisitos
- Debe estar **permitido** por el lenguaje
- Debe haber **suficiente información** para establecer la [[Ligadura|ligadura]] unívocamente (ej. por tipo de los operandos)

#### Ejemplo
```c
int i, j, k;
float a, b, c;
i = j + k;    // + suma enteros
a = b + c;    // + suma flotantes
```
Los **tipos** de las variables y los **parámetros** de las funciones permiten desambiguar en compilación.

#### Contraste con [[Alias]]

| Concepto | Relación |
| -------- | -------- |
| **Alias** | Distintos nombres → 1 entidad |
| **Sobrecarga** | 1 nombre → distintas entidades |

> Ver también: [[Alias]], [[Ligadura]], [[Atributo Tipo]]
