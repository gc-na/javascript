<!--
Meta Description: # MIDIOutputMap en JavaScript: Guía Completa ## Sinopsis `MIDIOutputMap` es un objeto en JavaScript que se utiliza dentro de la Web MIDI API para repr...
Meta Keywords: midi, midioutputmap, que, dispositivos, outputs
-->

# MIDIOutputMap en JavaScript: Guía Completa

## Sinopsis
`MIDIOutputMap` es un objeto en JavaScript que se utiliza dentro de la Web MIDI API para representar un mapa de salidas MIDI disponibles en el sistema. Permite a los desarrolladores interactuar con dispositivos de salida MIDI, facilitando la creación de aplicaciones musicales y de audio interactivas en la web.

## Documentación
`MIDIOutputMap` es una parte esencial de la Web MIDI API, que permite a los navegadores comunicarse con dispositivos MIDI. Este objeto es un `Map` que contiene pares de clave-valor, donde la clave es un identificador único para el dispositivo de salida y el valor es un objeto `MIDIOutput`, que representa la salida MIDI real.

### Propósito
La principal función de `MIDIOutputMap` es proporcionar a los desarrolladores acceso a todos los dispositivos de salida MIDI conectados, permitiendo enviar mensajes MIDI a estos dispositivos.

### Uso
Para acceder a `MIDIOutputMap`, primero es necesario solicitar acceso a las entradas y salidas MIDI mediante la función `navigator.requestMIDIAccess()`, que devuelve una promesa que se resuelve en un objeto `MIDIAccess`. Desde este objeto, se puede obtener el `MIDIOutputMap`.

```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const outputs = midiAccess.outputs;
    const outputMap = outputs; // Este es el MIDIOutputMap
});
```

### Detalles
- **Estructura**: `MIDIOutputMap` es un objeto tipo `Map`, lo que significa que puedes usar métodos como `.get()`, `.set()`, y `.has()` para manipularlo.
- **Iteración**: Puedes iterar sobre el mapa utilizando un bucle `for...of` o métodos como `.forEach()`.
- **Compatibilidad**: La Web MIDI API y, por ende, `MIDIOutputMap`, son compatibles con la mayoría de navegadores modernos, pero siempre es recomendable verificar la compatibilidad en el navegador específico que se utilizará.

## Ejemplos
### Ejemplo Básico de Acceso a MIDIOutputMap
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const outputs = midiAccess.outputs;
    
    outputs.forEach((output) => {
        console.log(`Nombre: ${output.name}, ID: ${output.id}`);
    });
});
```

### Ejemplo de Envío de Mensajes MIDI
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const outputs = midiAccess.outputs;
    const output = outputs.get('ID_DEL_DISPOSITIVO'); // Reemplaza con el ID real

    if (output) {
        output.send([144, 60, 0]); // Envía un mensaje de nota encendida
    }
});
```

## Explicación
### Errores Comunes y Notas Adicionales
- **Permisos**: Asegúrate de que el usuario haya otorgado permisos para acceder a los dispositivos MIDI. Sin estos permisos, el `MIDIAccess` no se resolverá correctamente.
- **No hay dispositivos**: Si no hay dispositivos de salida MIDI disponibles, el `MIDIOutputMap` estará vacío. Siempre verifica si el mapa tiene salidas antes de intentar interactuar con él.
- **Identificadores Únicos**: Los IDs de los dispositivos son únicos para cada sesión. Si un dispositivo se desconecta y se vuelve a conectar, puede tener un nuevo ID.

## Resumen en una línea
`MIDIOutputMap` es un objeto de la Web MIDI API en JavaScript que permite acceder y gestionar dispositivos de salida MIDI conectados al sistema.