---
aliases:
  - alcance dinámico
  - dynamic scope
---
El **alcance dinámico** define el alcance de una [[Variable]] en términos de la **ejecución del programa**. Cada declaración extiende su efecto sobre todas las instrucciones ejecutadas posteriormente, hasta que una nueva declaración con el mismo nombre sea encontrada.

#### Regla de búsqueda
Si una unidad necesita referenciar una variable no local, debe buscarla hacia afuera siguiendo la ejecución y viendo **quién llamó** a la unidad que la necesita.

#### Lenguajes que lo usan
APL, Lisp (original), Afnix (antes Aleph), TCL (Tool Command Language), Perl, Snobol4.

#### Desventajas
- Poco claras en cuanto a la programación
- Encontrar una declaración en el flujo de ejecución puede ser difícil
- El código se hace más difícil de leer, especialmente en programas grandes

> Contraste: [[Alcance Estático]]
> Ver también: [[Atributo Alcance]], [[Variable]]
