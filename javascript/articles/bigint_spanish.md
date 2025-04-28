<!--
Meta Description: # BigInt en JavaScript: Manejo de Números Enteros Grandes ## Sinopsis BigInt es un tipo de dato en JavaScript que permite representar números enteros ...
Meta Keywords: bigint, javascript, number, tipo, que
-->

# BigInt en JavaScript: Manejo de Números Enteros Grandes

## Sinopsis
BigInt es un tipo de dato en JavaScript que permite representar números enteros de gran tamaño que superan el límite del tipo Number, que es 2^53 - 1. Esto es especialmente útil en aplicaciones que requieren cálculos precisos con números extremadamente grandes.

## Documentación
### Propósito
BigInt se introdujo en JavaScript para solucionar las limitaciones del tipo Number en el manejo de números enteros grandes. Mientras que el tipo Number es un número de punto flotante de doble precisión, BigInt permite trabajar con enteros de tamaño arbitrario.

### Uso
Para crear un BigInt, puedes utilizar el sufijo `n` al final de un número entero o utilizar el constructor `BigInt()`. Por ejemplo:

```javascript
const bigInt1 = 123456789012345678901234567890n; // Usando el sufijo 'n'
const bigInt2 = BigInt("123456789012345678901234567890"); // Usando el constructor
```

### Detalles
- Los BigInt no pueden ser mezclados con números de tipo Number en operaciones matemáticas, a menos que se conviertan explícitamente.
- BigInt soporta operaciones aritméticas como suma, resta, multiplicación y división.
- No se pueden utilizar BigInt como claves de propiedades en objetos.

## Ejemplos
### Creación de BigInt
```javascript
const bigIntA = 9007199254740991n; // Máximo número seguro de JavaScript
const bigIntB = BigInt(12345); // Creación a partir de un número
```

### Operaciones Aritméticas
```javascript
const sum = bigIntA + bigIntB; // Suma
const product = bigIntA * bigIntB; // Multiplicación
```

### Comparaciones
```javascript
console.log(bigIntA === BigInt(9007199254740991)); // true
console.log(bigIntA > bigIntB); // true
```

## Explicación
### Errores Comunes
- **Mezcla de tipos**: Intentar sumar un BigInt y un Number sin conversión resultará en un error.
  ```javascript
  const number = 5;
  console.log(bigIntA + number); // TypeError: Cannot mix BigInt and other types
  ```

- **Uso en objetos**: No se pueden usar BigInt como claves de propiedades en objetos. En su lugar, se deben convertir a cadenas si se desea utilizarlos como claves.

### Notas Adicionales
- BigInt no tiene un límite superior práctico, pero su uso excesivo puede resultar en un rendimiento más lento comparado con el tipo Number.
- El uso de BigInt es ideal en aplicaciones financieras, criptografía, y cualquier otro dominio que requiera precisión en cálculos con grandes números.

## Resumen en una línea
BigInt es un tipo de dato en JavaScript que permite trabajar con números enteros de tamaño arbitrario, superando las limitaciones del tipo Number.