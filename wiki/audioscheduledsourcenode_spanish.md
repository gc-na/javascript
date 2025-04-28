<!--
Meta Description: # AudioScheduledSourceNode: Controlando el Audio en JavaScript ## Sinopsis `AudioScheduledSourceNode` es un nodo esencial de la API Web Audio que perm...
Meta Keywords: audio, audiocontext, que, nodo, reproducción
-->

# AudioScheduledSourceNode: Controlando el Audio en JavaScript

## Sinopsis

`AudioScheduledSourceNode` es un nodo esencial de la API Web Audio que permite generar y manipular audio programado en aplicaciones web. Este nodo es fundamental para crear experiencias sonoras interactivas y dinámicas en navegadores modernos.

## Documentación

### Propósito

`AudioScheduledSourceNode` es una clase base para nodos de audio que generan sonidos, como `AudioBufferSourceNode` y `ConstantSourceNode`. Utiliza un enfoque basado en eventos para programar la reproducción de audio en momentos específicos, lo que permite una gran flexibilidad en el control del audio.

### Uso

Para utilizar un `AudioScheduledSourceNode`, primero se debe crear una instancia de un nodo específico, como `AudioBufferSourceNode`. Este nodo se puede conectar a otros nodos de audio en el contexto de audio (`AudioContext`) para crear una cadena de procesamiento de audio.

#### Creación de un AudioScheduledSourceNode

```javascript
const audioContext = new AudioContext();
const source = audioContext.createBufferSource();
```

### Detalles

- **Métodos Importantes:**
  - `start(when)`: Inicia la reproducción del nodo a un tiempo específico. El parámetro `when` indica el tiempo en segundos desde el momento actual en el que debe comenzar la reproducción.
  - `stop(when)`: Detiene la reproducción del nodo a un tiempo específico.

- **Propiedades Clave:**
  - `buffer`: Permite asignar un `AudioBuffer` al nodo, el cual contiene los datos de audio que se reproducirán.
  - `playbackRate`: Controla la velocidad de reproducción del audio.

## Ejemplos

### Ejemplo Básico de Reproducción de Audio

```javascript
const audioContext = new AudioContext();
const source = audioContext.createBufferSource();

// Cargar un buffer de audio (debe hacerse de forma asíncrona)
fetch('ruta/a/tu/audio.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    source.buffer = buffer;
    source.connect(audioContext.destination);
    source.start(0); // Comienza inmediatamente
  })
  .catch(error => console.error('Error al cargar el audio:', error));
```

### Programación de la Reproducción

```javascript
const audioContext = new AudioContext();
const source = audioContext.createBufferSource();

// Supongamos que ya se ha cargado el buffer de audio
source.buffer = audioBuffer; // 'audioBuffer' es un AudioBuffer previamente cargado
source.connect(audioContext.destination);

// Programar el inicio de la reproducción en 2 segundos
source.start(audioContext.currentTime + 2);
```

## Explicación

Un error común al trabajar con `AudioScheduledSourceNode` es intentar iniciar la reproducción de un nodo después de que ha sido detenido. Una vez que un `AudioScheduledSourceNode` ha terminado su reproducción, no se puede reutilizar, y será necesario crear una nueva instancia del nodo para reproducir el audio nuevamente.

También es importante tener en cuenta que el `AudioContext` debe estar en estado "running" para que se pueda reproducir audio. Si el usuario ha interactuado con la página (por ejemplo, haciendo clic en un botón), se activará el `AudioContext`.

## Resumen en Una Frase

`AudioScheduledSourceNode` es un nodo clave en la API Web Audio de JavaScript que permite la generación y control programado de audio en aplicaciones web interactivas.