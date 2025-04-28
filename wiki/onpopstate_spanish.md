<!--
Meta Description: # onpopstate: Manejador de eventos de estado en la historia de JavaScript ## Sinopsis El evento `onpopstate` en JavaScript permite a los desarrollador...
Meta Keywords: evento, página, historial, onpopstate, que
-->

# onpopstate: Manejador de eventos de estado en la historia de JavaScript

## Sinopsis
El evento `onpopstate` en JavaScript permite a los desarrolladores manejar cambios en el historial del navegador, específicamente cuando el usuario navega hacia atrás o hacia adelante a través de la historia de páginas. Este evento es fundamental para la gestión de aplicaciones web de una sola página (SPA).

## Documentación
### Propósito
El evento `onpopstate` se activa en el objeto `window` cuando se activa una entrada en el historial, lo que significa que el usuario ha navegado a una página anterior o siguiente. Esto es especialmente útil para aplicaciones que utilizan la API de Historia, permitiendo a los desarrolladores actualizar la interfaz de usuario de la aplicación sin recargar la página.

### Uso
Para utilizar `onpopstate`, se debe asignar una función de manejo al evento. Esta función se ejecutará cada vez que se produzca un evento de `popstate`. A continuación se muestra la sintaxis básica:

```javascript
window.onpopstate = function(event) {
    // Lógica a ejecutar cuando se produce el evento
};
```

### Detalles
- **Evento**: `popstate`
- **Propiedades del evento**:
  - `state`: contiene el estado asociado con la entrada del historial que se ha activado.
  
Este evento solo se dispara para los estados que han sido añadidos al historial mediante `history.pushState()` o `history.replaceState()`. No se activa por el evento de carga inicial de la página.

## Ejemplos
### Ejemplo Básico
```javascript
// Agregar un estado al historial
history.pushState({page: 1}, "Página 1", "?page=1");

window.onpopstate = function(event) {
    if (event.state) {
        console.log("Estado actual:", event.state);
    } else {
        console.log("No hay estado asociado.");
    }
};

// Navegar hacia atrás en el historial
history.back();  // Esto activará el evento onpopstate
```

### Ejemplo con Múltiples Estados
```javascript
// Agregar múltiples estados al historial
history.pushState({page: 1}, "Página 1", "?page=1");
history.pushState({page: 2}, "Página 2", "?page=2");

window.onpopstate = function(event) {
    if (event.state) {
        document.title = "Página " + event.state.page;
    }
};

// Cambiar de página en el historial
history.back();  // Al volver, cambiará el título a "Página 1"
history.forward(); // Al avanzar, cambiará el título a "Página 2"
```

## Explicación
### Errores Comunes
- **No detectar el evento**: Asegúrate de que el evento `popstate` está correctamente vinculado al objeto `window`.
- **Uso de `state`**: Recuerda que `event.state` puede ser `null` si no se ha añadido un estado usando `pushState` o `replaceState`.
- **Historial inicial**: El evento `popstate` no se dispara en la carga inicial de la página. Esto puede causar confusión si se espera que el estado se maneje en esa fase.

### Notas Adicionales
- `onpopstate` solo se activa al navegar por el historial, no al hacer clic en enlaces o al cargar una nueva página.
- Es recomendable manejar los cambios de estado de forma efectiva para evitar que los usuarios experimenten un comportamiento inesperado en la navegación.

## Resumen en Una Línea
El evento `onpopstate` permite manejar cambios en el historial del navegador en aplicaciones JavaScript, facilitando la navegación sin recargas de página.