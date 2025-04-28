<!--
Meta Description: # MIDIPort en JavaScript: Todo lo que Necesitas Saber ## Sinopsis MIDIPort es una interfaz clave en la API Web MIDI que permite a los desarrolladores ...
Meta Keywords: midi, que, puerto, midiaccess, midiport
-->

# MIDIPort en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
MIDIPort es una interfaz clave en la API Web MIDI que permite a los desarrolladores de JavaScript interactuar con dispositivos MIDI (Musical Instrument Digital Interface) en el navegador. Facilita la comunicación entre aplicaciones web y hardware musical.

## Documentación
### Propósito
La interfaz MIDIPort representa un puerto MIDI que puede ser de entrada o salida. Permite el envío y la recepción de mensajes MIDI, lo que habilita a las aplicaciones web para controlar dispositivos musicales, sintetizadores y otros equipos que utilizan el protocolo MIDI.

### Uso
Para utilizar MIDIPort, primero debes acceder a la API Web MIDI. Esto se realiza a través del método `navigator.requestMIDIAccess()`, que devuelve un objeto `MIDIAccess`. A partir de ahí, puedes obtener una lista de puertos MIDI disponibles.

#### Ejemplo de uso:
```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
  const inputs = midiAccess.inputs;
  const outputs = midiAccess.outputs;

  inputs.forEach((input) => {
    console.log(`Puerto de entrada: ${input.name}`);
  });

  outputs.forEach((output) => {
    console.log(`Puerto de salida: ${output.name}`);
  });
}

function onMIDIFailure() {
  console.error('No se pudo acceder a los dispositivos MIDI.');
}
```

### Detalles
- **Propiedades**:
  - `id`: Un identificador único para el puerto.
  - `name`: El nombre del puerto.
  - `state`: El estado del puerto (`"connected"` o `"disconnected"`).
  - `type`: El tipo de puerto (`"input"` o `"output"`).

- **Métodos**:
  - `send(data)`: Envía un mensaje MIDI a través del puerto.
  - `close()`: Cierra el puerto MIDI.

## Ejemplos
### Envío de un mensaje MIDI
```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess);

function onMIDISuccess(midiAccess) {
  const output = midiAccess.outputs.get('nombre_del_puerto_de_salida');
  const noteOn = [0x90, 60, 0x7f]; // Nota C4
  output.send(noteOn); // Envía la nota
}
```

### Recepción de mensajes MIDI
```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess);

function onMIDISuccess(midiAccess) {
  const input = midiAccess.inputs.get('nombre_del_puerto_de_entrada');
  input.onmidimessage = (message) => {
    console.log(`Mensaje MIDI recibido: ${message.data}`);
  };
}
```

## Explicación
Al trabajar con MIDIPort, es importante tener en cuenta que la API Web MIDI solo está disponible en navegadores compatibles como Chrome y Edge. Además, asegúrate de que el usuario ha dado permiso para acceder a los dispositivos MIDI. Un error común es intentar enviar mensajes sin verificar si el puerto está conectado o disponible, lo que puede causar fallos en la ejecución.

## Resumen en una línea
MIDIPort es la interfaz en JavaScript que permite la comunicación con dispositivos MIDI a través de la API Web MIDI.