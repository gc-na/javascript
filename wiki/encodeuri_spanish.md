<!--
Meta Description: # encodeURI en JavaScript: Codificación de URI para la Web ## Sinopsis `encodeURI` es una función de JavaScript que permite codificar una URI (Identif...
Meta Keywords: uri, que, una, encodeuri, javascript
-->

# encodeURI en JavaScript: Codificación de URI para la Web

## Sinopsis
`encodeURI` es una función de JavaScript que permite codificar una URI (Identificador Uniforme de Recursos) convirtiendo caracteres especiales en su representación hexadecimal, lo que asegura que la URI sea válida y pueda ser transmitida correctamente.

## Documentación

### Propósito
La función `encodeURI` se utiliza para codificar una URI completa, asegurando que los caracteres que tienen un significado especial en las URIs (como `:`, `/`, `?`, `&`, `=`) no se modifiquen. Esto es crucial para el correcto funcionamiento de las solicitudes web y para evitar errores al acceder a recursos.

### Uso
La sintaxis de `encodeURI` es la siguiente:

```javascript
encodeURI(uri)
```

- **uri**: Una cadena de texto que representa una URI que se desea codificar.

### Detalles
- `encodeURI` no codifica caracteres reservados que tienen un significado especial en una URI. Por ejemplo, no transformará `&`, `=`, `?`, `#`, etc.
- Si se necesita codificar una parte de la URI, como los parámetros de consulta, se debe utilizar `encodeURIComponent`, que codifica todos los caracteres especiales.

## Ejemplos

### Ejemplo Básico
```javascript
const uri = "https://example.com/mi página?parametro=valor con espacios";
const uriCodificada = encodeURI(uri);
console.log(uriCodificada); // "https://example.com/mi%20p%C3%A1gina?parametro=valor%20con%20espacios"
```

### Ejemplo con Caracteres Especiales
```javascript
const uri = "https://example.com/búsqueda?query=JavaScript & Otros";
const uriCodificada = encodeURI(uri);
console.log(uriCodificada); // "https://example.com/b%C3%BAqueda?query=JavaScript & Otros"
```

## Explicación
Al utilizar `encodeURI`, es importante tener en cuenta que algunos caracteres no se codificarán, ya que son necesarios para la estructura de la URI. Por ejemplo, si se intenta codificar la cadena `https://example.com/?search=JavaScript&lang=es`, el símbolo `&` no se convertirá. Esto puede llevar a confusiones si se espera que todos los caracteres sean codificados.

### Consideraciones
- Para codificar componentes individuales de una URI, como los parámetros de consulta o segmentos de ruta, se debe utilizar `encodeURIComponent`.
- Si se pasa un valor que no es una cadena, `encodeURI` lo convertirá automáticamente a cadena utilizando `String()`.

## Resumen en una línea
`encodeURI` es una función de JavaScript que codifica una URI para que sea válida y se pueda utilizar en solicitudes web, sin alterar los caracteres reservados.