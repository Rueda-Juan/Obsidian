---
aliases:
  - alias
  - aliases
---
Un **alias** se produce cuando **variables distintas comparten un mismo objeto** en el mismo entorno de referencia. Sus caminos de acceso conducen al mismo objeto, por lo que una modificación a través de un nombre afecta a todos.

#### Ejemplo en C
```c
int x = 5;
int *px = &x;
int *py = px;    // py también apunta a x
*px = 10;        // efecto colateral: x, *px y *py son todos 10
```

#### Ventajas
- Compartir objetos para mejorar la **eficiencia**

#### Desventajas
- El valor se puede modificar **sin usar su nombre**
- Programas difíciles de **leer y depurar**
- Generan **efectos colaterales** no evidentes

> Se recomienda **no usar alias**.

#### Contraste con [[Sobrecarga]]

| Concepto | Relación |
| -------- | -------- |
| **Alias** | Distintos nombres → 1 entidad |
| **Sobrecarga** | 1 nombre → distintas entidades |

> Ver también: [[Puntero]], [[Variable]], [[Sobrecarga]]
