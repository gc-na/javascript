<!--
Meta Description: # onprogress: Evento de Progreso en JavaScript ## Sinopsis El evento `onprogress` en JavaScript se utiliza para gestionar el seguimiento del progreso ...
Meta Keywords: xhr, onprogress, evento, progreso, carga
-->

# onprogress: Evento de Progreso en JavaScript

## Sinopsis
El evento `onprogress` en JavaScript se utiliza para gestionar el seguimiento del progreso de operaciones asíncronas, como la descarga de archivos o la carga de recursos. Este evento permite a los desarrolladores proporcionar retroalimentación al usuario sobre el estado de las operaciones en curso.

## Documentación
El evento `onprogress` es parte de la interfaz de la API `XMLHttpRequest` y también se encuentra en la API de `Fetch` y en `HTML5` para elementos multimedia como `<audio>` y `<video>`. Su propósito principal es notificar a los desarrolladores sobre el progreso de la carga o descarga de un recurso.

### Propósito
El evento `onprogress` se dispara periódicamente durante el proceso de carga, proporcionando información sobre el progreso actual en términos de bytes transferidos y el tamaño total del recurso.

### Uso
Para utilizar el evento `onprogress`, se debe agregar un listener al objeto que se desea monitorear. Este listener recibirá un objeto `ProgressEvent` que contiene información sobre el progreso.

```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'archivo.txt', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const porcentaje = (event.loaded / event.total) * 100;
        console.log(`Carga: ${porcentaje.toFixed(2)}% completada`);
    }
};

xhr.onload = function() {
    if (xhr.status === 200) {
        console.log('Carga completada con éxito');
    }
};

xhr.send();
```

## Ejemplos
### Ejemplo 1: Uso básico con XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'archivo-grande.zip', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const porcentaje = (event.loaded / event.total) * 100;
        console.log(`Progreso: ${porcentaje.toFixed(2)}%`);
    }
};

xhr.onload = function() {
    console.log('Descarga finalizada');
};

xhr.send();
```

### Ejemplo 2: Uso con elementos multimedia
```javascript
const video = document.querySelector('video');
video.onprogress = function() {
    const buffered = video.buffered;
    if (buffered.length > 0) {
        const porcentaje = (buffered.end(0) / video.duration) * 100;
        console.log(`Progreso del video: ${porcentaje.toFixed(2)}%`);
    }
};
```

## Explicación
Al utilizar `onprogress`, es importante tener en cuenta que este evento puede no proporcionar información precisa si el recurso no tiene un tamaño conocido (por ejemplo, streaming de datos). Además, el evento se puede activar varias veces durante la carga, lo que significa que los desarrolladores deben manejar adecuadamente la frecuencia de actualizaciones para evitar sobrecargar la interfaz de usuario.

### Errores comunes
- Ignorar la propiedad `lengthComputable`, que indica si se puede calcular el porcentaje de progreso. Si esta propiedad es falsa, no se debe intentar calcular el porcentaje.
- No manejar adecuadamente los casos en los que la carga falla o se interrumpe. Siempre es recomendable añadir un manejador para el evento `onerror`.

## Resumen en una frase
El evento `onprogress` en JavaScript permite a los desarrolladores monitorear el progreso de operaciones asíncronas, mejorando la experiencia del usuario durante la carga o descarga de recursos.