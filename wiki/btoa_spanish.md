<!--
Meta Description: # btoa: Convertir Cadena a Base64 en JavaScript ## Sinopsis La función `btoa` en JavaScript se utiliza para codificar una cadena de texto en su repres...
Meta Keywords: btoa, que, cadena, base64, javascript
-->

# btoa: Convertir Cadena a Base64 en JavaScript

## Sinopsis
La función `btoa` en JavaScript se utiliza para codificar una cadena de texto en su representación Base64, lo que permite la transmisión segura de datos binarios a través de medios que manejan texto, como JSON o URLs.

## Documentación
### Propósito
`btoa` (Binary to ASCII) convierte una cadena de texto en su equivalente en Base64. Esta función es especialmente útil cuando se necesita enviar datos binarios a través de medios que solo soportan texto.

### Uso
La función `btoa` se puede utilizar de la siguiente manera:

```javascript
let base64String = btoa(string);
```

**Parámetros:**
- `string`: Una cadena de texto (de tipo `string`) que se desea convertir a Base64. Debe consistir únicamente en caracteres ASCII.

**Retorno:**
- Devuelve una nueva cadena que representa los datos codificados en Base64.

### Detalles
- `btoa` solo acepta cadenas de texto que contengan caracteres ASCII. Si la cadena contiene caracteres Unicode, se debe convertir a un formato compatible antes de usar `btoa`.
- La función `btoa` es parte de la interfaz global de JavaScript, lo que significa que está disponible en todos los entornos que soportan JavaScript, como navegadores web y Node.js (aunque en Node.js se recomienda usar `Buffer` para la codificación Base64).

## Ejemplos
### Ejemplo Básico
```javascript
let originalString = "Hola, Mundo!";
let encodedString = btoa(originalString);
console.log(encodedString); // Resultado: "SG9sYSwgTXVuZG8h"
```

### Ejemplo con Caracteres Especiales
Para usar `btoa` con caracteres Unicode, primero se deben codificar adecuadamente:
```javascript
function utf8ToB64(str) {
    return btoa(unescape(encodeURIComponent(str)));
}

let originalString = "¡Hola, Mundo!";
let encodedString = utf8ToB64(originalString);
console.log(encodedString); // Resultado: "wqFIb2xhLCBNdW5kbyE="
```

## Explicación
### Errores Comunes
- **Caracteres no ASCII:** Si intentas utilizar `btoa` con caracteres que no son ASCII, se lanzará un `InvalidCharacterError`. Por lo tanto, es esencial convertir cualquier texto Unicode a su representación ASCII antes de usar `btoa`.
  
### Notas Adicionales
- Para decodificar una cadena Base64 de vuelta a su forma original, se utiliza la función `atob`, que realiza la operación inversa.
- Asegúrate de que la cadena de entrada sea una cadena válida y no esté vacía para evitar errores.

## Resumen en Una Línea
La función `btoa` en JavaScript se utiliza para codificar cadenas de texto en formato Base64, facilitando la transmisión de datos binarios a través de medios textuales.