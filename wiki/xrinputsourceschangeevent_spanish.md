<!--
Meta Description: # XRInputSourcesChangeEvent: Evento de Cambio de Fuentes de Entrada en JavaScript ## Sinopsis El `XRInputSourcesChangeEvent` es un evento en JavaScrip...
Meta Keywords: entrada, evento, fuentes, las, event
-->

# XRInputSourcesChangeEvent: Evento de Cambio de Fuentes de Entrada en JavaScript

## Sinopsis
El `XRInputSourcesChangeEvent` es un evento en JavaScript que se activa cuando hay un cambio en las fuentes de entrada de realidad virtual o aumentada en un entorno WebXR. Este evento permite a los desarrolladores gestionar y responder a cambios en los dispositivos de entrada, como controladores o dispositivos de seguimiento de manos.

## Documentación
### Propósito
El `XRInputSourcesChangeEvent` tiene como objetivo notificar a las aplicaciones de realidad virtual y aumentada sobre cambios en los dispositivos de entrada disponibles. Esto puede incluir la adición o eliminación de controladores y otros dispositivos relacionados.

### Uso
Para utilizar el `XRInputSourcesChangeEvent`, los desarrolladores deben añadir un event listener en un objeto `XRSession`. El evento proporciona información sobre las fuentes de entrada actuales y permite actualizar la interfaz de usuario o el estado de la aplicación en consecuencia.

#### Sintaxis
```javascript
session.addEventListener('inputsourceschange', (event) => {
    // Manejo del evento
});
```

### Detalles
- **Propiedades del Evento**: El evento incluye detalles sobre las fuentes de entrada involucradas en el cambio.
- **Compatibilidad**: Asegúrese de que su entorno WebXR esté correctamente configurado y que el dispositivo soporte la API de WebXR.
- **Desencadenado**: Este evento se desencadena en situaciones como la conexión o desconexión de controladores de realidad virtual.

## Ejemplos
### Ejemplo 1: Escuchar Cambios en las Fuentes de Entrada
```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('inputsourceschange', (event) => {
        const inputSources = event.inputSources;
        inputSources.forEach(source => {
            console.log(`ID de fuente de entrada: ${source.id}`);
        });
    });
});
```

### Ejemplo 2: Manejo de Fuentes de Entrada
```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('inputsourceschange', (event) => {
        event.added.forEach(source => {
            console.log(`Controlador agregado: ${source.handedness}`);
        });
        event.removed.forEach(source => {
            console.log(`Controlador eliminado: ${source.id}`);
        });
    });
});
```

## Explicación
- **Errores Comunes**: Asegúrate de que el contexto de la sesión XR esté activo antes de añadir el listener para evitar errores de referencia.
- **Gestión de Estado**: Es importante manejar adecuadamente el estado de las fuentes de entrada para garantizar que la experiencia del usuario sea fluida y sin interrupciones.
- **Rendimiento**: Evita realizar operaciones pesadas dentro del manejador del evento, ya que esto puede afectar el rendimiento general de la aplicación.

## Resumen en Una Línea
El `XRInputSourcesChangeEvent` en JavaScript permite a los desarrolladores gestionar cambios en las fuentes de entrada de realidad virtual y aumentada, mejorando la interactividad y la experiencia del usuario.