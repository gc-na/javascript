<!--
Meta Description: # TextDecoder: Decodificador de Texto en JavaScript ## Sinopsis `TextDecoder` es una interfaz de JavaScript que permite decodificar datos codificados ...
Meta Keywords: textdecoder, texto, que, javascript, datos
-->

# TextDecoder: Decodificador de Texto en JavaScript

## Sinopsis
`TextDecoder` es una interfaz de JavaScript que permite decodificar datos codificados en diferentes formatos de texto, como UTF-8, UTF-16, entre otros. Su uso es fundamental para convertir datos binarios en cadenas de texto legibles.

## Documentación
### Propósito
`TextDecoder` es parte de la API de codificación de texto en JavaScript, diseñada para facilitar la transformación de datos binarios en texto. Esto es especialmente útil al trabajar con datos recibidos a través de la red o archivos binarios que necesitan ser interpretados como texto.

### Uso
Para utilizar `TextDecoder`, primero debes instanciar un objeto de esta clase, especificando el tipo de codificación que quieres utilizar. A continuación, puedes llamar al método `.decode()` para convertir un `ArrayBuffer` o un `TypedArray` en una cadena de texto.

#### Sintaxis
```javascript
const decoder = new TextDecoder(encoding, options);
const text = decoder.decode(input);
```

- **encoding**: (opcional) Una cadena que representa la codificación que se usará para decodificar, como "utf-8" o "utf-16". Por defecto, es "utf-8".
- **options**: (opcional) Un objeto que puede incluir propiedades como `fatal` y `ignoreBOM`.

### Ejemplo
```javascript
// Ejemplo básico de uso de TextDecoder
const buffer = new Uint8Array([72, 101, 108, 108, 111]);
const decoder = new TextDecoder('utf-8');
const text = decoder.decode(buffer);

console.log(text); // Output: "Hello"
```

### Explicación
Al trabajar con `TextDecoder`, es importante tener en cuenta lo siguiente:

1. **Codificaciones Soportadas**: No todas las codificaciones son compatibles con todos los navegadores. Asegúrate de verificar la compatibilidad si trabajas con codificaciones menos comunes.
   
2. **Manejo de Errores**: Si se establece la opción `fatal` en `true`, el `TextDecoder` lanzará un error si encuentra un carácter no válido. Si es `false`, ignorará los caracteres no válidos.

3. **Uso Eficiente de Memoria**: Al decodificar grandes volúmenes de datos, considera el uso de `TextDecoder` en un contexto donde la gestión de la memoria sea crítica, ya que puede consumir recursos significativos.

## Resumen en Una Línea
`TextDecoder` en JavaScript es una herramienta esencial para convertir datos binarios en texto legible, soportando múltiples codificaciones.