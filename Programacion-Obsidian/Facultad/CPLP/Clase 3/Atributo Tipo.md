---
aliases:
  - tipo
  - atributo tipo
  - tipos de datos
---
El **tipo** de una [[Variable]] especifica:
1. El **conjunto de valores posibles** que se pueden asociar
2. El **conjunto de operaciones permitidas** sobre ella (crear, acceder, modificar)

Antes de referenciar una variable hay que ligarle el tipo. Una variable de un tipo dado es una **instancia** de ese tipo.

#### Importancia
- **Protege** de operaciones no permitidas
- Permite **chequeo de tipos**
- Ayuda a la **detección temprana de errores** y la **confiabilidad**

#### [[Clases de Tipo]]
- **Predefinidos:** tipos base del lenguaje (int, float, boolean)
- **Definidos por el usuario:** nuevos tipos a partir de bases y constructores
- **[[Tipo Abstracto de Datos|TAD]]:** tipo con operaciones públicas y representación privada

#### [[Momento de Ligadura Variable-Tipo]]

| Momento | Binding time | ¿Se puede cambiar? | Lenguajes |
| ------- | ------------ | ------------------- | --------- |
| **Estático** | Compilación | No | C, Pascal, Java, ADA |
| **Dinámico** | Ejecución | Sí | Python, Ruby, JavaScript |

Formas de ligadura estática: **explícita**, **implícita** e **inferida**.

> Ver también: [[Variable]], [[Ligadura]], [[Clases de Tipo]]
