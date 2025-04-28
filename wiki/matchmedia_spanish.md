<!--
Meta Description: # matchMedia: API de JavaScript para Consultas de Media ## Sinopsis `matchMedia` es una función de JavaScript que permite evaluar si una consulta de m...
Meta Keywords: que, matchmedia, media, una, consulta
-->

# matchMedia: API de JavaScript para Consultas de Media

## Sinopsis
`matchMedia` es una función de JavaScript que permite evaluar si una consulta de media CSS se cumple o no, y se utiliza comúnmente para adaptar el comportamiento de una página web según el tamaño de la pantalla o las características del dispositivo.

## Documentación
La función `matchMedia` forma parte de la interfaz `Window` y se utiliza para crear un objeto `MediaQueryList`. Este objeto representa el resultado de una consulta de media, permitiendo a los desarrolladores escuchar cambios en el estado de la consulta de media.

### Propósito
El propósito de `matchMedia` es proporcionar una manera de aplicar estilos y comportamientos específicos en función de las características del dispositivo, como el ancho, la orientación o la resolución de la pantalla.

### Uso
La sintaxis básica para utilizar `matchMedia` es la siguiente:

```javascript
const mediaQueryList = window.matchMedia(mediaQueryString);
```

- **mediaQueryString**: Una cadena que contiene la consulta de media a evaluar (por ejemplo, `"(max-width: 600px)"`).

### Propiedades importantes
- **matches**: Devuelve un booleano que indica si la consulta de media actual se cumple.
- **media**: Devuelve la consulta de media que se pasó a `matchMedia`.
- **addListener**: Método que permite registrar un listener que se activará cuando el estado de la consulta cambie.
- **removeListener**: Método que permite eliminar un listener previamente registrado.

## Ejemplos

### Ejemplo básico
```javascript
const mediaQueryList = window.matchMedia("(max-width: 600px)");

if (mediaQueryList.matches) {
    console.log("La pantalla es más estrecha que 600px.");
} else {
    console.log("La pantalla es más ancha que 600px.");
}
```

### Uso con listeners
```javascript
const mediaQueryList = window.matchMedia("(max-width: 600px)");

function handleMediaChange(event) {
    if (event.matches) {
        console.log("El ancho de pantalla es menor o igual a 600px.");
    } else {
        console.log("El ancho de pantalla es mayor a 600px.");
    }
}

// Agregar listener
mediaQueryList.addListener(handleMediaChange);

// Llamar la función inicialmente
handleMediaChange(mediaQueryList);
```

## Explicación
Al utilizar `matchMedia`, es crucial entender que los listeners se activan cada vez que cambia el estado de la consulta de media. Sin embargo, es importante tener en cuenta que `addListener` está obsoleto y se recomienda utilizar `addEventListener` para una mayor compatibilidad futura. También, asegúrate de limpiar los listeners cuando ya no sean necesarios para evitar pérdidas de memoria.

```javascript
mediaQueryList.addEventListener("change", handleMediaChange);
```

Además, es posible que algunos navegadores antiguos no soporten `matchMedia`, por lo que es recomendable verificar la compatibilidad antes de implementarlo.

## Resumen en una línea
`matchMedia` es una función de JavaScript que permite evaluar consultas de media CSS y reaccionar a cambios en el tamaño de pantalla o características del dispositivo.