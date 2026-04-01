---
aliases:
  - análisis semántico
  - analizador semántico
---
El **análisis semántico** es la tercera fase de la [[Etapa de Análisis]] de un [[Compilación|compilador]]. Se ejecuta después del [[Análisis Léxico|Scanner]] y el [[Análisis Sintáctico|Parser]], trabajando sobre las estructuras ya reconocidas.

Verifica que el programa tenga **significado válido** según las reglas del lenguaje y agrega **información semántica** (tipos, alcance, referencias).

#### Funciones principales
- **Comprobación y control de tipos** (compatibilidad entre variables, expresiones y operaciones)
- **Gestión de la [[Tabla de Símbolos]]:** agregar atributos como tipo (int, float), alcance (local, global), clase de identificador (variable, función, constante)
- **Verificación de nombres:** variables declaradas o no antes de usarse, control de duplicados en un mismo ámbito
- **Aplicación de reglas semánticas** mediante [[Gramática de Atributos|gramáticas de atributos]] y [[Árbol Sintáctico Atribuido|árboles atribuidos]]

Es **puente** entre la [[Etapa de Análisis]] y la [[Etapa de Síntesis]].

> Ver también: [[Semántica Estática]], [[Análisis Léxico]], [[Análisis Sintáctico]]
