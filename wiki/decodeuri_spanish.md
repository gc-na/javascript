<!--
Meta Description: # decodeURI en JavaScript: Decodificación de URIs de manera efectiva ## Sinopsis `decodeURI` es una función en JavaScript que se utiliza para decodifi...
Meta Keywords: decodeuri, una, que, javascript, para
-->

# decodeURI en JavaScript: Decodificación de URIs de manera efectiva

## Sinopsis
`decodeURI` es una función en JavaScript que se utiliza para decodificar componentes de una URI (Identificador Uniforme de Recursos) previamente codificados. Es fundamental para la manipulación de URL y se utiliza frecuentemente en aplicaciones web.

## Documentación
### Propósito
La función `decodeURI` se utiliza para decodificar una cadena que ha sido codificada con `encodeURI`. Esto es útil para interpretar correctamente los caracteres especiales que forman parte de la URI.

### Uso
La sintaxis para utilizar `decodeURI` es la siguiente:

```javascript
decodeURI(encodedURI)
```

- **encodedURI**: Una cadena que representa una URI codificada.

### Detalles
- `decodeURI` no decodifica los caracteres reservados en una URI, como `#`, `?` y `&`. Estos caracteres tienen significados especiales en las URIs y su decodificación podría alterar el significado de la URI.
- Para decodificar un componente específico de una URI, se debe utilizar `decodeURIComponent`, que sí decodifica estos caracteres reservados.

## Ejemplos
### Ejemplo 1: Decodificación básica
```javascript
const uriCodificada = "https%3A%2F%2Fwww.ejemplo.com%2Fpagina%3Fid%3D123";
const uriDecodificada = decodeURI(uriCodificada);
console.log(uriDecodificada); // https://www.ejemplo.com/pagina?id=123
```

### Ejemplo 2: Decodificación de caracteres especiales
```javascript
const uriCodificada = "Hola%20Mundo%21";
const uriDecodificada = decodeURI(uriCodificada);
console.log(uriDecodificada); // Hola Mundo!
```

### Ejemplo 3: Uso en una URL con caracteres reservados
```javascript
const uriCodificada = "https%3A%2F%2Fwww.ejemplo.com%2Fbuscar%3Fquery%3DJavaScript%26pagina%3D1";
const uriDecodificada = decodeURI(uriCodificada);
console.log(uriDecodificada); // https://www.ejemplo.com/buscar?query=JavaScript&pagina=1
```

## Explicación
Es importante tener en cuenta que `decodeURI` no debe ser utilizado para decodificar partes de una URI que contienen caracteres reservados. En su lugar, se debe emplear `decodeURIComponent` para evitar errores en la interpretación de la URI. Además, si se pasa a `decodeURI` una cadena que no está correctamente codificada, la función puede devolver un resultado inesperado o incluso lanzar un error en ciertos navegadores.

## Resumen en una línea
`decodeURI` es una función en JavaScript que decodifica componentes de URIs codificadas, preservando los caracteres reservados.