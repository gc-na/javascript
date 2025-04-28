<!--
Meta Description: # MIDIConnectionEvent en JavaScript: Conexión y Desconexión de Dispositivos MIDI ## Sinopsis El evento `MIDIConnectionEvent` en JavaScript permite a l...
Meta Keywords: midi, port, dispositivos, console, los
-->

# MIDIConnectionEvent en JavaScript: Conexión y Desconexión de Dispositivos MIDI

## Sinopsis
El evento `MIDIConnectionEvent` en JavaScript permite a los desarrolladores detectar cuando un dispositivo MIDI se conecta o se desconecta del sistema, facilitando la interacción con dispositivos musicales electrónicos.

## Documentación
El `MIDIConnectionEvent` es parte de la API Web MIDI, que proporciona un medio para interactuar con dispositivos MIDI desde el navegador. Este evento se dispara cada vez que un dispositivo MIDI se conecta o se desconecta. Es especialmente útil para aplicaciones musicales y de producción que requieren la detección y gestión dinámica de dispositivos MIDI.

### Propósito
El propósito de `MIDIConnectionEvent` es permitir a los desarrolladores manejar eventos relacionados con la conexión de dispositivos MIDI. Esto incluye la posibilidad de actualizar la interfaz de usuario, iniciar o detener la transmisión de datos MIDI, o configurar dispositivos de manera dinámica.

### Uso
Para utilizar el `MIDIConnectionEvent`, primero necesitas asegurarte de que la API Web MIDI esté disponible en el navegador. Luego, puedes añadir un escuchador de eventos a la interfaz MIDI que responda a los cambios de conexión.

```javascript
if (navigator.requestMIDIAccess) {
    navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);
}

function onMIDISuccess(midiAccess) {
    midiAccess.onstatechange = handleStateChange;
}

function handleStateChange(event) {
    const { port } = event;
    if (port.state === 'connected') {
        console.log(`Dispositivo MIDI conectado: ${port.name}`);
    } else if (port.state === 'disconnected') {
        console.log(`Dispositivo MIDI desconectado: ${port.name}`);
    }
}

function onMIDIFailure() {
    console.error('No se pudo acceder a los dispositivos MIDI.');
}
```

## Ejemplos
### Ejemplo básico de conexión y desconexión
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    midiAccess.onstatechange = (event) => {
        const port = event.port;
        if (port.state === 'connected') {
            console.log(`Conectado: ${port.name}`);
        } else if (port.state === 'disconnected') {
            console.log(`Desconectado: ${port.name}`);
        }
    };
}).catch((error) => {
    console.error('Error al acceder a MIDI:', error);
});
```

### Ejemplo de manejo de múltiples dispositivos
```javascript
function handleStateChange(event) {
    const port = event.port;
    if (port.state === 'connected') {
        console.log(`Dispositivo conectado: ${port.name} (${port.type})`);
    } else if (port.state === 'disconnected') {
        console.log(`Dispositivo desconectado: ${port.name} (${port.type})`);
    }
}
```

## Explicación
### Errores comunes
- **Compatibilidad del navegador**: No todos los navegadores soportan la API Web MIDI. Asegúrate de probar en un navegador que tenga esta funcionalidad habilitada.
- **Permisos**: Algunos navegadores requieren permisos adicionales para acceder a dispositivos MIDI. Asegúrate de que se han concedido los permisos necesarios.
- **Interacción con otros eventos**: Al manejar eventos de conexión y desconexión, considera cómo interactúan con otros eventos MIDI, como la recepción de mensajes MIDI.

## Resumen en una línea
El `MIDIConnectionEvent` permite a los desarrolladores de JavaScript gestionar la conexión y desconexión de dispositivos MIDI, mejorando la interactividad en aplicaciones musicales.