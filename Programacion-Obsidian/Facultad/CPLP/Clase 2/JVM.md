---
aliases:
  - Java Virtual Machine
  - máquina virtual de Java
---
La **JVM** (Java Virtual Machine) es una máquina virtual que ejecuta el **bytecode** generado por el compilador de Java. Es un ejemplo de [[Traducción Híbrida]] donde se combina [[Compilación]] (a código intermedio) con [[Interpretación]] (ejecución del bytecode).

#### Flujo
1. El compilador de Java genera **bytecode** (código intermedio independiente de la plataforma)
2. La JVM interpreta o compila (**JIT**) el bytecode a código de máquina nativo
3. Esto permite que los programas sean **portables** entre distintas arquitecturas

> Ver también: [[Traducción Híbrida]], [[Compilación]], [[Interpretación]]
