<!--
Meta Description: # parseInt en JavaScript: Guía Completa y Ejemplos ## Sinopsis `parseInt` es una función de JavaScript que se utiliza para convertir cadenas de texto ...
Meta Keywords: parseint, que, javascript, base, cadena
-->

# parseInt en JavaScript: Guía Completa y Ejemplos

## Sinopsis
`parseInt` es una función de JavaScript que se utiliza para convertir cadenas de texto en números enteros. Permite especificar la base numérica para la conversión, lo que la hace versátil en el manejo de diferentes sistemas numéricos.

## Documentación
### Propósito
La función `parseInt` se utiliza para analizar una cadena y devolver un entero. Es especialmente útil cuando se trabaja con datos que provienen de formularios o APIs en formato de texto que necesitan ser convertidos a un número para realizar cálculos o comparaciones.

### Uso
La sintaxis de `parseInt` es la siguiente:

```javascript
parseInt(string, radix);
```

- **string**: La cadena que se desea convertir a un número entero.
- **radix** (opcional): Un entero entre 2 y 36 que representa la base numérica en la que se interpretan los números. Si se omite, se asume que es 10 (decimal) en la mayoría de los casos, pero puede ser 16 (hexadecimal) si la cadena comienza con "0x".

### Detalles
- `parseInt` ignora los espacios en blanco al inicio de la cadena.
- Si la cadena no puede ser convertida a un número, `parseInt` devolverá `NaN` (Not a Number).
- Si el primer carácter no es un dígito válido en la base indicada, se devolverá `NaN`.

## Ejemplos
### Ejemplo 1: Conversión básica
```javascript
let numero = parseInt("42");
console.log(numero); // Salida: 42
```

### Ejemplo 2: Especificando la base
```javascript
let numeroHex = parseInt("0x1A", 16);
console.log(numeroHex); // Salida: 26
```

### Ejemplo 3: Ignorando espacios
```javascript
let numeroConEspacios = parseInt("   100   ");
console.log(numeroConEspacios); // Salida: 100
```

### Ejemplo 4: Devolviendo NaN
```javascript
let noNumero = parseInt("abc");
console.log(noNumero); // Salida: NaN
```

## Explicación
Al utilizar `parseInt`, es importante tener en cuenta algunos errores comunes:

- **No especificar la base**: Si no se especifica la base y la cadena comienza con "0", el comportamiento puede ser confuso, ya que en algunos navegadores se interpretará como octal (base 8) en lugar de decimal.
  
- **Uso de NaN**: Cuando se intenta analizar una cadena que no comienza con un dígito válido, el resultado será `NaN`. Es recomendable verificar el resultado con `isNaN()` para evitar errores en cálculos posteriores.

- **Valores truncados**: `parseInt` solo devuelve la parte entera del número. Si se intenta convertir un número decimal, se truncará la parte fraccionaria.

## Resumen en una línea
`parseInt` es una función de JavaScript que convierte cadenas en números enteros, permitiendo especificar la base numérica para la conversión.