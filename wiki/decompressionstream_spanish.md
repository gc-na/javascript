<!--
Meta Description: # DecompressionStream en JavaScript: Descompresión de flujos de datos ## Sinopsis `DecompressionStream` es una interfaz de JavaScript que permite la d...
Meta Keywords: decompressionstream, que, datos, response, javascript
-->

# DecompressionStream en JavaScript: Descompresión de flujos de datos

## Sinopsis
`DecompressionStream` es una interfaz de JavaScript que permite la descompresión de flujos de datos codificados, facilitando la manipulación eficiente de datos comprimidos en aplicaciones web.

## Documentación

### Propósito
`DecompressionStream` se utiliza para descomprimir datos que han sido previamente comprimidos utilizando algoritmos compatibles, como GZIP o DEFLATE. Esta funcionalidad es especialmente útil en aplicaciones web que manejan grandes volúmenes de datos, ya que permite reducir el tamaño de las cargas útiles y mejorar los tiempos de carga.

### Uso
Para utilizar `DecompressionStream`, primero se debe crear una instancia de esta clase. Luego, se puede utilizar junto con la API de Streams de JavaScript para descomprimir datos a medida que se reciben. 

#### Sintaxis
```javascript
const decompressionStream = new DecompressionStream(algorithm);
```
Donde `algorithm` es una cadena que especifica el algoritmo de descompresión a utilizar, como `"gzip"` o `"deflate"`.

### Detalles
- **Compatibilidad:** Asegúrate de que el navegador soporta la API de `DecompressionStream` antes de su uso.
- **Manejo de flujos:** `DecompressionStream` trabaja mejor con flujos de lectura y escritura, permitiendo procesar datos en tiempo real.

## Ejemplos

### Ejemplo básico de uso
```javascript
async function obtenerDatosDescomprimidos(url) {
    const response = await fetch(url);
    const reader = response.body.getReader();
    const decompressionStream = new DecompressionStream('gzip');
    const stream = response.body.pipeThrough(decompressionStream);
    const text = await new Response(stream).text();
    console.log(text);
}
```

### Descompresión de datos en una solicitud de red
```javascript
fetch('data.gz')
    .then(response => {
        const decompressionStream = new DecompressionStream('gzip');
        return response.body.pipeThrough(decompressionStream);
    })
    .then(stream => new Response(stream))
    .then(response => response.text())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```

## Explicación
Al utilizar `DecompressionStream`, es importante tener en cuenta que los datos de entrada deben estar en un formato comprimido compatible. Un error común es intentar descomprimir datos que no están en el formato esperado, lo que resulta en errores de ejecución. Además, la implementación de esta característica puede variar entre diferentes navegadores, por lo que es recomendable verificar la compatibilidad antes de su uso.

## Resumen en una línea
`DecompressionStream` es una interfaz de JavaScript que permite descomprimir flujos de datos comprimidos, mejorando la eficiencia en el manejo de grandes volúmenes de información en aplicaciones web.