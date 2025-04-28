<!--
Meta Description: # AggregateError en JavaScript: Manejo de Errores Agrupados ## Sinopsis `AggregateError` es una clase en JavaScript que se utiliza para manejar múltip...
Meta Keywords: error, aggregateerror, errores, que, errors
-->

# AggregateError en JavaScript: Manejo de Errores Agrupados

## Sinopsis
`AggregateError` es una clase en JavaScript que se utiliza para manejar múltiples errores en operaciones asincrónicas, especialmente en el contexto de Promesas. Permite agrupar varios errores en un solo objeto, facilitando su manejo y comprensión.

## Documentación
### Propósito
`AggregateError` se introdujo en ECMAScript 2021 y su propósito es proporcionar una forma estructurada de manejar múltiples errores que pueden surgir de operaciones asincrónicas que se ejecutan en paralelo.

### Uso
La clase `AggregateError` recibe un array de errores como argumento y los encapsula en un solo objeto que puede ser lanzado o manejado. Esto es especialmente útil en operaciones que pueden fallar de manera independiente, como en la función `Promise.all()`.

### Sintaxis
```javascript
class AggregateError extends Error {
    constructor(errors, message) {
        super(message);
        this.errors = errors; // Array de errores
    }
}
```

### Propiedades
- `errors`: Un array que contiene todos los errores que se agruparon.
- `message`: Mensaje de error que describe el problema.

## Ejemplos
### Ejemplo 1: Uso básico de AggregateError
```javascript
async function example() {
    const promises = [
        Promise.reject(new Error("Error 1")),
        Promise.reject(new Error("Error 2")),
        Promise.resolve("Éxito")
    ];

    try {
        await Promise.all(promises);
    } catch (error) {
        if (error instanceof AggregateError) {
            console.log("Se encontraron múltiples errores:");
            error.errors.forEach(err => console.log(err.message));
        } else {
            console.log("Un error ocurrió:", error.message);
        }
    }
}

example();
```

### Ejemplo 2: Creando un AggregateError manualmente
```javascript
const errors = [
    new Error("Error A"),
    new Error("Error B"),
    new Error("Error C")
];

const aggregateError = new AggregateError(errors, "Se encontraron múltiples errores.");
console.log(aggregateError.message); // "Se encontraron múltiples errores."
console.log(aggregateError.errors.length); // 3
```

## Explicación
### Problemas Comunes
1. **No Capturar Todos los Errores**: Cuando se utilizan promesas en paralelo, es fácil olvidar manejar todos los errores. `AggregateError` ayuda a consolidar estos errores para que no se pierda información crítica.
  
2. **Confusión con el Manejo de Errores**: Si no se verifica si el error es una instancia de `AggregateError`, podrías perder la oportunidad de manejar múltiples errores de forma efectiva.

3. **Compatibilidad**: Asegúrate de que tu entorno de ejecución soporte ECMAScript 2021, ya que `AggregateError` no está disponible en versiones anteriores de JavaScript.

## Resumen en una Frase
`AggregateError` es una clase en JavaScript que permite agrupar múltiples errores de operaciones asincrónicas en un solo objeto, facilitando su manejo y comprensión.