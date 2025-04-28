<!--
Meta Description: # Evento MediaQueryListEvent en JavaScript: Uso y Ejemplos ## Sinopsis El evento `MediaQueryListEvent` en JavaScript permite a los desarrolladores rea...
Meta Keywords: para, mediaquerylistevent, medios, que, listener
-->

# Evento MediaQueryListEvent en JavaScript: Uso y Ejemplos

## Sinopsis
El evento `MediaQueryListEvent` en JavaScript permite a los desarrolladores reaccionar a cambios en las consultas de medios, facilitando la implementación de diseños responsivos que se adaptan a diferentes tamaños de pantalla y configuraciones de dispositivos.

## Documentación
### Propósito
El `MediaQueryListEvent` es un objeto que se genera cuando se produce un cambio en la evaluación de una consulta de medios, que puede ser definida a través de la API `matchMedia()`. Esto es especialmente útil para la adaptación de estilos y comportamientos en aplicaciones web que requieren un diseño flexible.

### Uso
Para utilizar `MediaQueryListEvent`, primero debes crear una instancia de `MediaQueryList` utilizando `window.matchMedia()`. Luego, puedes añadir un listener para escuchar los cambios en el estado de la consulta de medios. Cuando se produce un cambio, se disparará un evento `MediaQueryListEvent`.

### Detalles
- **Propiedades**:
  - `matches`: Un booleano que indica si la consulta de medios actual se cumple.
  - `media`: Una cadena que representa la consulta de medios utilizada.

- **Métodos**:
  - `addListener()`: Método obsoleto para añadir un listener.
  - `addEventListener()`: Método moderno para añadir un listener de eventos.
  - `removeListener()`: Método obsoleto para eliminar un listener.
  - `removeEventListener()`: Método moderno para eliminar un listener de eventos.

## Ejemplos
### Ejemplo básico de uso
```javascript
// Crear una consulta de medios
const mediaQuery = window.matchMedia('(max-width: 600px)');

// Función para manejar el evento
function handleMediaChange(event) {
    if (event.matches) {
        console.log('La pantalla es menor o igual a 600px');
    } else {
        console.log('La pantalla es mayor a 600px');
    }
}

// Añadir el listener
mediaQuery.addEventListener('change', handleMediaChange);

// Llamar la función inicialmente
handleMediaChange(mediaQuery);
```

### Ejemplo con CSS
```javascript
const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)');

function handleColorSchemeChange(event) {
    if (event.matches) {
        document.body.classList.add('dark-mode');
    } else {
        document.body.classList.remove('dark-mode');
    }
}

mediaQuery.addEventListener('change', handleColorSchemeChange);
handleColorSchemeChange(mediaQuery);
```

## Explicación
Al usar `MediaQueryListEvent`, es importante tener en cuenta que algunos navegadores pueden no soportar los métodos `addEventListener` y `removeEventListener` en versiones antiguas. En estos casos, se recomienda usar `addListener` y `removeListener`, aunque están obsoletos. Además, asegúrate de limpiar los listeners cuando ya no sean necesarios para evitar posibles fugas de memoria.

## Resumen en una línea
`MediaQueryListEvent` en JavaScript permite manejar cambios en consultas de medios para facilitar diseños responsivos y adaptativos en aplicaciones web.