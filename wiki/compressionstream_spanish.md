<!--
Meta Description: # CompressionStream en JavaScript: Compresión de Datos en el Navegador ## Sinopsis `CompressionStream` es una interfaz de JavaScript que permite la co...
Meta Keywords: compressionstream, const, compresión, datos, una
-->

# CompressionStream en JavaScript: Compresión de Datos en el Navegador

## Sinopsis
`CompressionStream` es una interfaz de JavaScript que permite la compresión de datos en el navegador utilizando algoritmos de compresión como GZIP. Esta funcionalidad es especialmente útil para optimizar el rendimiento de aplicaciones web al reducir el tamaño de los datos transmitidos.

## Documentación
`CompressionStream` es parte de la API de Streams de JavaScript, introducida para facilitar la manipulación de datos en flujo. Su propósito principal es proporcionar una forma sencilla de comprimir datos al volcarlos a un flujo de salida.

### Propósito
La API `CompressionStream` permite a los desarrolladores comprimir datos en tiempo real, lo que resulta en un uso más eficiente del ancho de banda y una carga más rápida de las aplicaciones.

### Uso
Para utilizar `CompressionStream`, debes crear una instancia de la clase y luego usarla en combinación con flujos de lectura y escritura.

#### Sintaxis
```javascript
const compressionStream = new CompressionStream('gzip');
```

#### Métodos
- **write()**: Permite escribir datos en el flujo.
- **close()**: Finaliza el flujo de compresión.

### Detalles
- Los datos deben ser proporcionados en forma de `ReadableStream`.
- El método de compresión soportado por `CompressionStream` es `gzip`.
- `CompressionStream` es compatible con navegadores modernos, pero es recomendable verificar su disponibilidad antes de utilizarla.

## Ejemplos

### Ejemplo 1: Compresión de una cadena
```javascript
async function compressData(data) {
    const stream = new CompressionStream('gzip');
    const writer = stream.getWriter();
    
    writer.write(new TextEncoder().encode(data));
    writer.close();
    
    const compressedStream = stream.readable;
    const compressedData = await streamToString(compressedStream);
    return compressedData;
}

async function streamToString(stream) {
    const reader = stream.getReader();
    let result = '';
    let done, value;
    
    while ({ done, value } = await reader.read(), !done) {
        result += new TextDecoder().decode(value);
    }
    return result;
}

compressData("Texto a comprimir").then(console.log);
```

### Ejemplo 2: Uso con Fetch API
```javascript
async function fetchAndCompress(url) {
    const response = await fetch(url);
    const reader = response.body.getReader();
    const compressionStream = new CompressionStream('gzip');
    const writer = compressionStream.getWriter();

    let result = '';
    let { done, value };
    
    while ({ done, value } = await reader.read(), !done) {
        writer.write(value);
    }
    writer.close();
    
    const compressedStream = compressionStream.readable;
    result = await streamToString(compressedStream);
    return result;
}

fetchAndCompress('https://ejemplo.com/dato').then(console.log);
```

## Explicación
Al utilizar `CompressionStream`, es importante tener en cuenta algunos detalles:

- **Compatibilidad**: No todos los navegadores soportan `CompressionStream`. Verifica la compatibilidad en [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/CompressionStream).
- **Manejo de Errores**: Maneja adecuadamente los errores que pueden surgir al escribir en el flujo o al cerrar el flujo de compresión.
- **Eficiencia**: Aunque la compresión puede mejorar el rendimiento, también puede introducir una sobrecarga en el procesamiento. Evalúa si la compresión es necesaria para tus datos.

## Resumen en una línea
`CompressionStream` es una interfaz en JavaScript que permite la compresión de datos en tiempo real en el navegador, optimizando así la transmisión de información.