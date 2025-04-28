<!--
Meta Description: # URIError en JavaScript: Manejo de Errores de Codificación de URI ## Sinopsis El **URIError** en JavaScript es un tipo de error que se produce cuando...
Meta Keywords: urierror, que, javascript, uri, error
-->

# URIError en JavaScript: Manejo de Errores de Codificación de URI

## Sinopsis
El **URIError** en JavaScript es un tipo de error que se produce cuando hay un problema al codificar o decodificar un URI (Identificador Uniforme de Recursos). Este error es fundamental para el manejo adecuado de las funciones relacionadas con la manipulación de URIs.

## Documentación
### Propósito
El **URIError** es parte de la jerarquía de errores de JavaScript y se lanza específicamente en situaciones relacionadas con las funciones `encodeURI()`, `encodeURIComponent()`, `decodeURI()`, y `decodeURIComponent()`. Se utiliza para indicar que una operación relacionada con la codificación o decodificación de un URI ha fallado.

### Uso
El **URIError** se lanza automáticamente cuando se intenta decodificar un URI que no está correctamente formado. Por ejemplo, si se pasa un carácter no válido a las funciones de decodificación, se generará un **URIError**. 

#### Ejemplo de Uso
```javascript
try {
    decodeURIComponent('%'); // Intento de decodificación incorrecto
} catch (e) {
    if (e instanceof URIError) {
        console.error('Se produjo un URIError: ' + e.message);
    }
}
```

### Detalles
- **Instanciación**: Puedes instanciar un `URIError` usando `new URIError(message)`, donde `message` es un mensaje opcional que describe el error.
- **Propiedades**: Un `URIError` tiene propiedades como `name` (que siempre será 'URIError') y `message` (un mensaje descriptivo del error).

## Ejemplos
### Ejemplo 1: Uso Correcto
```javascript
const uri = 'https://example.com/?name=John%20Doe';
const decodedURI = decodeURIComponent(uri);
console.log(decodedURI); // "https://example.com/?name=John Doe"
```

### Ejemplo 2: Uso Incorrecto
```javascript
try {
    decodeURIComponent('%20%ZZ'); // Carácter no válido en la codificación
} catch (e) {
    console.error('Error capturado: ' + e); // Captura el URIError
}
```

## Explicación
Al trabajar con URIs, es importante asegurarse de que los datos sean válidos y estén correctamente codificados. Comúnmente, los desarrolladores pueden encontrar errores al intentar decodificar cadenas que contienen caracteres no válidos o mal formados. Por ejemplo, el uso de un carácter `%` sin un par de dígitos hexadecimales puede resultar en un **URIError**. 

### Trampas Comunes
- **Decodificación de Cadenas Mal Formadas**: Siempre verifica que las cadenas que intentas decodificar estén correctamente formadas.
- **No Capturar Errores**: Ignorar el manejo de excepciones puede resultar en fallos silenciosos en la aplicación. Es recomendable usar bloques `try-catch` para capturar y manejar **URIError** adecuadamente.

## Resumen en Una Línea
El **URIError** en JavaScript se produce al intentar codificar o decodificar un URI mal formado, facilitando el manejo de errores en la manipulación de URIs.