<!--
Meta Description: # Números en JavaScript: Todo lo que Necesitas Saber ## Sinopsis El tipo de dato "Number" en JavaScript es fundamental para realizar operaciones aritm...
Meta Keywords: números, javascript, que, let, nan
-->

# Números en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
El tipo de dato "Number" en JavaScript es fundamental para realizar operaciones aritméticas y trabajar con valores numéricos. Este tipo de dato puede representar tanto enteros como números de punto flotante, así como valores especiales como `Infinity`, `-Infinity`, y `NaN`.

## Documentación

### Propósito
El tipo "Number" se utiliza para almacenar y manipular datos numéricos en JavaScript. Permite realizar cálculos matemáticos, comparaciones y operaciones lógicas.

### Uso
En JavaScript, los números se pueden definir de diversas maneras:
- Números enteros: `let entero = 5;`
- Números de punto flotante: `let decimal = 3.14;`
- Notación científica: `let cientifico = 1.5e3; // equivalente a 1500`

### Detalles
- **Representación**: Todos los números en JavaScript son representados como números de doble precisión (64 bits).
- **Rango**: El rango de valores que se pueden representar es de aproximadamente -1.7976931348623157e+308 a 1.7976931348623157e+308.
- **Valores especiales**:
  - `Infinity`: Representa un número infinito.
  - `-Infinity`: Representa un número negativo infinito.
  - `NaN`: Significa "Not-a-Number", que se utiliza para representar valores que no son números.

## Ejemplos

```javascript
// Ejemplo de número entero
let entero = 10;
console.log(entero); // Salida: 10

// Ejemplo de número de punto flotante
let decimal = 7.5;
console.log(decimal); // Salida: 7.5

// Ejemplo de notación científica
let cientifico = 2e3; // 2000
console.log(cientifico); // Salida: 2000

// Ejemplo de Infinity
let infinito = 1 / 0;
console.log(infinito); // Salida: Infinity

// Ejemplo de NaN
let noNumero = 0 / 0;
console.log(noNumero); // Salida: NaN
```

## Explicación
Al trabajar con números en JavaScript, es importante tener en cuenta algunos aspectos:
- **Precisión**: Los números de punto flotante pueden llevar a errores de precisión. Por ejemplo, `0.1 + 0.2 !== 0.3` debido a la forma en que se almacenan los números en memoria.
- **Operaciones**: Al realizar operaciones, asegúrate de que los operandos son del tipo correcto. Por ejemplo, concatenar un número y una cadena resultará en una cadena.
- **NaN**: Cualquier operación que involucre `NaN` resultará en `NaN`, lo que puede ser confuso.

## Resumen en una línea
El tipo "Number" en JavaScript es esencial para manejar valores numéricos, permitiendo realizar cálculos y operaciones aritméticas de manera eficiente.