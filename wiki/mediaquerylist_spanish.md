<!--
Meta Description: # MediaQueryList en JavaScript: Cómo Detectar Cambios en el Tamaño de Pantalla ## Sinopsis `MediaQueryList` es una interfaz de JavaScript que permite ...
Meta Keywords: mediaquerylist, cambios, medios, console, log
-->

# MediaQueryList en JavaScript: Cómo Detectar Cambios en el Tamaño de Pantalla

## Sinopsis
`MediaQueryList` es una interfaz de JavaScript que permite a los desarrolladores interactuar con las consultas de medios (media queries) de CSS, facilitando la detección de cambios en el tamaño de la ventana del navegador y la aplicación de estilos o comportamientos dinámicos en función de las condiciones especificadas.

## Documentación
### Propósito
`MediaQueryList` se utiliza para consultar el estado de las condiciones de media queries definidas en CSS. Permite a los desarrolladores saber si una consulta de medios está activa o no, y reaccionar a los cambios en tiempo real.

### Uso
Para utilizar `MediaQueryList`, se emplea el método `window.matchMedia()`, que recibe como parámetro una cadena que representa la consulta de medios. Este método devuelve un objeto `MediaQueryList`, que tiene dos propiedades principales:

- `matches`: un booleano que indica si la consulta de medios es verdadera.
- `media`: una cadena que representa la consulta de medios utilizada.

Además, `MediaQueryList` proporciona un método para manejar cambios en la coincidencia de la consulta mediante el evento `change`.

### Detalles
```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');

if (mediaQueryList.matches) {
    console.log("La pantalla es menor o igual a 600px.");
} else {
    console.log("La pantalla es mayor a 600px.");
}

// Escuchar cambios
mediaQueryList.addEventListener('change', (event) => {
    if (event.matches) {
        console.log("Cambio: La pantalla ahora es menor o igual a 600px.");
    } else {
        console.log("Cambio: La pantalla ahora es mayor a 600px.");
    }
});
```

## Ejemplos
### Ejemplo Básico
```javascript
const mq = window.matchMedia('(min-width: 768px)');

if (mq.matches) {
    console.log('La pantalla es suficientemente ancha.');
} else {
    console.log('La pantalla es demasiado estrecha.');
}
```

### Ejemplo con Evento de Cambio
```javascript
const mediaQuery = window.matchMedia('(orientation: portrait)');

function handleOrientationChange(event) {
    if (event.matches) {
        console.log('El dispositivo está en modo retrato.');
    } else {
        console.log('El dispositivo está en modo paisaje.');
    }
}

// Agregar el listener
mediaQuery.addEventListener('change', handleOrientationChange);

// Llamar a la función inicialmente
handleOrientationChange(mediaQuery);
```

## Explicación
### Errores Comunes
1. **No Escuchar Cambios:** Un error común es no agregar un evento listener para detectar cambios en la consulta de medios. Esto puede resultar en que el comportamiento de la aplicación no se actualice cuando el tamaño de la ventana cambia.
   
2. **Uso Incorrecto de Propiedades:** Asegúrate de utilizar `matches` y `media` correctamente. Por ejemplo, confundir `media` con la evaluación de la consulta podría llevar a resultados inesperados.

### Notas Adicionales
- `MediaQueryList` es compatible con la mayoría de los navegadores modernos, pero siempre es recomendable verificar la compatibilidad si se trabaja en entornos más antiguos.
- Utilizar consultas de medios bien definidas puede mejorar el rendimiento y la experiencia del usuario en aplicaciones responsivas.

## Resumen en Una Línea
`MediaQueryList` permite a los desarrolladores detectar y reaccionar a cambios en las condiciones de las consultas de medios en JavaScript.