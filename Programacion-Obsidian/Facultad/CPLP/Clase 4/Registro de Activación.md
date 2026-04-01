---
aliases:
  - registro de activación
  - registros de activación
  - R.A.
  - RA
  - activation record
---
El **registro de activación** (R.A.) es la zona de **memoria de datos** que almacena los **datos locales** de una [[Rutina|unidad]] durante su ejecución. Su contenido es **cambiante** (varía en cada invocación).

#### Contenido
- **Variables locales** de la rutina
- **Punto de retorno:** dirección de la instrucción a la que se debe volver tras finalizar la rutina
- **Valor de retorno** (en caso de funciones)
- Enlace al ambiente no local (según la [[Estructura de Ejecución]])

#### Alocación

| [[Estructura de Ejecución]] | Alocación del R.A. |
| --------- | ------------------ |
| Estática (C1, C2) | Antes de la ejecución; tamaño fijo |
| Basada en pila | Automáticamente al invocar, se desaloca al terminar |
| Dinámica | En el heap cuando se necesita |

> Ver también: [[Segmento de Código]], [[Instancia de Unidad]], [[Procesador Abstracto]], [[Rutina]]
