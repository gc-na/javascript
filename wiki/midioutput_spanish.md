<!--
Meta Description: # MIDIOutput en JavaScript: Controla la salida MIDI en aplicaciones web ## Sinopsis MIDIOutput es una interfaz de programación en JavaScript que permi...
Meta Keywords: midi, los, web, dispositivos, mensajes
-->

# MIDIOutput en JavaScript: Controla la salida MIDI en aplicaciones web

## Sinopsis
MIDIOutput es una interfaz de programación en JavaScript que permite a los desarrolladores interactuar con dispositivos MIDI, facilitando el envío de mensajes MIDI desde aplicaciones web. Esta funcionalidad es crucial para la creación de aplicaciones musicales y de audio interactivas.

## Documentación
### Propósito
MIDIOutput forma parte de la Web MIDI API, que permite a los navegadores web comunicarse con dispositivos MIDI. Esta API es especialmente útil para músicos y desarrolladores que desean integrar la tecnología MIDI en aplicaciones web, permitiendo la manipulación y transmisión de información musical en tiempo real.

### Uso
Para utilizar MIDIOutput, primero debes solicitar acceso a los dispositivos MIDI conectados. Esto se logra a través de la función `navigator.requestMIDIAccess()`, que devuelve un objeto `MIDIAccess`. A partir de este objeto, puedes acceder a las salidas MIDI disponibles y enviar mensajes a un dispositivo específico.

### Detalles
- **Métodos Principales:**
  - `send(data: Uint8Array | Array<number>, timestamp?: number)`: Envía un mensaje MIDI a la salida.
  - `clear()`: Elimina todos los mensajes en cola.

- **Propiedades:**
  - `id`: Identificador único de la salida MIDI.
  - `name`: Nombre del dispositivo MIDI.

## Ejemplos
### Ejemplo Básico de Uso
```javascript
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    const outputs = midiAccess.outputs;
    const output = outputs.get('nombre-del-dispositivo'); // Sustituir por el ID del dispositivo

    // Enviar un mensaje de nota encendida (note on)
    output.send([0x90, 60, 0x7f]); // Canal 1, Nota 60, Velocidad 127
}

function onMIDIFailure() {
    console.error('No se pudo acceder a los dispositivos MIDI.');
}
```

### Ejemplo de Mensaje de Nota Apagada
```javascript
// Apagar la nota (note off)
output.send([0x80, 60, 0x40]); // Canal 1, Nota 60, Velocidad 64
```

## Explicación
- **Errores Comunes:** Uno de los errores más comunes es no tener permisos para acceder a los dispositivos MIDI. Asegúrate de ejecutar tu aplicación en un entorno seguro, como HTTPS, para evitar problemas de acceso.
- **Compatibilidad:** La Web MIDI API no está soportada en todos los navegadores. Verifica la compatibilidad antes de implementar funciones MIDI en tu aplicación.
- **Optimización de Mensajes:** Al enviar mensajes MIDI, asegúrate de que los datos estén en el formato correcto para evitar comportamientos inesperados.

## Resumen en una Línea
MIDIOutput permite enviar mensajes MIDI desde aplicaciones web, facilitando la integración de dispositivos musicales en un entorno JavaScript.