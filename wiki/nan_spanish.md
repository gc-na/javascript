<!--
Meta Description: # NaN en JavaScript: Todo lo que necesitas saber ## Sinopsis NaN (Not a Number) es un valor especial en JavaScript que representa un valor que no es u...
Meta Keywords: nan, que, isnan, number, número
-->

# NaN en JavaScript: Todo lo que necesitas saber

## Sinopsis
NaN (Not a Number) es un valor especial en JavaScript que representa un valor que no es un número. Se utiliza comúnmente en operaciones que fallan al intentar convertir un valor en un número.

## Documentación
### Propósito
NaN es parte del estándar IEEE 754 para la representación de números de punto flotante, y en JavaScript, se utiliza para indicar que una operación numérica ha fallado o que un valor no se puede interpretar como un número.

### Uso
- **Tipo**: NaN es un tipo de dato de número (Number) en JavaScript.
- **Verificación**: Para verificar si un valor es NaN, se debe utilizar la función `isNaN()` o `Number.isNaN()`, ya que NaN no es igual a sí mismo (`NaN === NaN` es false).
  
### Detalles
- NaN es el único valor en JavaScript que no es igual a sí mismo. Esto significa que se puede utilizar como una señal de error en cálculos.
- NaN es el resultado de operaciones matemáticas que no pueden producir un número válido, como dividir 0 entre 0 o convertir una cadena no numérica a un número.
- Es importante tener en cuenta que `isNaN()` convierte su argumento a un número antes de hacer la verificación, mientras que `Number.isNaN()` no lo hace.

## Ejemplos
```javascript
// Ejemplo 1: División por cero
let resultado = 0 / 0; // resultado es NaN
console.log(resultado); // NaN

// Ejemplo 2: Conversión de una cadena no numérica
let conversion = Number("texto"); // conversion es NaN
console.log(conversion); // NaN

// Ejemplo 3: Uso de isNaN
console.log(isNaN(resultado)); // true
console.log(isNaN(conversion)); // true

// Ejemplo 4: Uso de Number.isNaN
console.log(Number.isNaN(resultado)); // true
console.log(Number.isNaN("texto")); // false
```

## Explicación
Un error común es pensar que NaN es igual a cero o a otro número. Sin embargo, NaN es único y solo se puede verificar como tal utilizando `isNaN()` o `Number.isNaN()`. También es importante recordar que NaN puede aparecer en situaciones inesperadas, como al intentar realizar operaciones con valores no numéricos.

Además, debido a su naturaleza, NaN puede propagarse en operaciones matemáticas. Por ejemplo, cualquier operación que incluya NaN también resultará en NaN:

```javascript
let a = 5;
let b = NaN;
let c = a + b; // c es NaN
console.log(c); // NaN
```

Es recomendable manejar NaN adecuadamente en el código para evitar errores silenciosos y asegurar que las operaciones numéricas se comporten como se espera.

## Resumen en una línea
NaN es un valor en JavaScript que indica que un resultado no es un número válido, y se utiliza para manejar errores en operaciones numéricas.