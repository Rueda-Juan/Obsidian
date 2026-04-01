---
aliases:
  - R-valor
  - r-valor
  - r-value
  - atributo r-valor
---
El **R-valor** de una [[Variable]] es el **valor codificado** almacenado en la ubicación ([[Atributo L-Valor|L-valor]]) asociada a la variable. La codificación se interpreta de acuerdo con el [[Atributo Tipo|tipo]].

```
R-Valor: 01110011
→ como int: número entero
→ como char: cadena de caracteres
```

#### Objeto = (L-valor, R-valor)
En `x := x + 1`, el lado izquierdo se refiere al **L-valor** (ubicación) y el derecho al **R-valor** (valor).

#### Ligadura de variable a valor
- **Dinámico:** el R-valor puede cambiar con asignaciones (`a := 17`)
- **Constante:** el R-valor se congela, no puede cambiarse

#### Momento de ligadura de constantes por lenguaje

| Lenguaje | Binding time | ¿Permite expresiones con variables? |
| -------- | ------------ | ------------------------------------ |
| **Pascal** | Compilación | No (`const c = x + 1` → ERROR) |
| **C** | Ejecución | Sí (`const int c = x + 1` → OK) |
| **ADA** | Ejecución | Sí (`c : constant := x` → OK) |

#### Inicialización
| Estrategia | Descripción |
| ---------- | ----------- |
| Por defecto | Enteros → 0, chars → blanco |
| En la declaración | `int i = 0;` / `I : Integer := 0;` |
| Ignorar | Toma lo que hay en memoria (riesgoso) |

> Ver también: [[Variable]], [[Atributo L-Valor]], [[Puntero|Punteros]]
