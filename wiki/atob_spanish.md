<!--
Meta Description: # atob: Decodificador de Base64 en JavaScript ## Sinopsis El método `atob` en JavaScript se utiliza para decodificar cadenas de texto que han sido cod...
Meta Keywords: que, atob, base64, javascript, cadenas
-->

# atob: Decodificador de Base64 en JavaScript

## Sinopsis
El método `atob` en JavaScript se utiliza para decodificar cadenas de texto que han sido codificadas en Base64. Este método es fundamental para la manipulación de datos en aplicaciones web que requieren la transferencia de datos codificados.

## Documentación
### Propósito
`atob` es una función global que permite convertir cadenas de texto codificadas en Base64 a su representación original. Su nombre proviene de "ASCII to binary", lo que refleja su función de conversión.

### Uso
La sintaxis básica de `atob` es la siguiente:

```javascript
atob(encodedString);
```

- **encodedString**: Una cadena de texto que representa datos codificados en Base64. Debe ser una cadena válida, de lo contrario, lanzará un error.

### Detalles
- `atob` solo puede decodificar cadenas en Base64 que contengan caracteres ASCII. 
- El resultado de `atob` es una cadena de texto que representa los datos originales en su forma no codificada.
- Si la cadena de entrada no es válida, se lanzará un `InvalidCharacterError`.

## Ejemplos
### Ejemplo Básico
```javascript
let encoded = "SGVsbG8gV29ybGQ="; // "Hello World" en Base64
let decoded = atob(encoded);
console.log(decoded); // Salida: "Hello World"
```

### Ejemplo con Caracteres Especiales
```javascript
let encoded = "JUMwJUEwJCUwJDEw"; // "¡Hola Mundo!" en Base64
let decoded = atob(encoded);
console.log(decoded); // Salida: "¡Hola Mundo!"
```

### Ejemplo de Manejo de Errores
```javascript
try {
    let invalidEncoded = "InvalidBase64!";
    let decoded = atob(invalidEncoded);
} catch (e) {
    console.error("Error de decodificación: " + e.message); // Salida: Error de decodificación: The string to be decoded is not correctly encoded.
}
```

## Explicación
Un punto importante a considerar es que `atob` no realiza ninguna verificación en la cadena, por lo que si se pasan caracteres no válidos, generará un error. Además, es importante recordar que `atob` trabaja con cadenas de texto que están codificadas en Base64, por lo que es fundamental asegurarse de que la entrada sea válida.

Otro aspecto a tener en cuenta es que `atob` no es compatible con datos binarios o cadenas que contengan caracteres fuera del rango ASCII. Para manejar datos binarios, es recomendable usar otras técnicas que impliquen el uso de `Uint8Array` y `TextDecoder`.

## Resumen en una Frase
`atob` es un método de JavaScript que decodifica cadenas de texto codificadas en Base64 a su forma original.