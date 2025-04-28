<!--
Meta Description: # AudioBufferSourceNode en JavaScript: Todo lo que Necesitas Saber ## Sinopsis El `AudioBufferSourceNode` es una parte fundamental de la API de Web Au...
Meta Keywords: audio, audiobuffersourcenode, que, audiocontext, source
-->

# AudioBufferSourceNode en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
El `AudioBufferSourceNode` es una parte fundamental de la API de Web Audio de JavaScript, diseñada para reproducir audio almacenado en un `AudioBuffer`. Este nodo permite la manipulación de audio de alta calidad en aplicaciones web, permitiendo a los desarrolladores crear experiencias de sonido dinámicas e interactivas.

## Documentación
### Propósito
El `AudioBufferSourceNode` permite reproducir audio almacenado en un `AudioBuffer`. Es un nodo de origen que, al ser conectado a un contexto de audio, puede iniciar la reproducción de un sonido, además de ofrecer características como la posibilidad de bucle y control de tiempo.

### Uso
Para utilizar un `AudioBufferSourceNode`, primero necesitas un contexto de audio (`AudioContext`) y un `AudioBuffer` que contenga los datos de audio que deseas reproducir. Una vez que tengas estos elementos, puedes crear una instancia del `AudioBufferSourceNode`, cargar los datos de audio, y controlar la reproducción.

### Detalles
- **Métodos principales**:
  - `start([when], [offset], [duration])`: Inicia la reproducción del audio.
  - `stop([when])`: Detiene la reproducción.
  
- **Propiedades**:
  - `loop`: Un booleano que indica si la reproducción debe reiniciarse una vez finalizada.
  - `loopEnd`: El tiempo, en segundos, donde termina el bucle.
  - `loopStart`: El tiempo, en segundos, donde comienza el bucle.

## Ejemplos
### Ejemplo básico de uso
```javascript
// Crear un contexto de audio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Cargar un archivo de audio
fetch('ruta/a/tu/audio.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    // Crear un AudioBufferSourceNode
    const source = audioContext.createBufferSource();
    source.buffer = buffer;

    // Conectar el nodo a la salida del audio
    source.connect(audioContext.destination);
    
    // Iniciar la reproducción
    source.start();
  })
  .catch(error => console.error('Error al cargar el audio:', error));
```

### Ejemplo de uso con bucle
```javascript
// Crear un contexto de audio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Cargar un archivo de audio
fetch('ruta/a/tu/audio.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    // Crear un AudioBufferSourceNode
    const source = audioContext.createBufferSource();
    source.buffer = buffer;
    
    // Activar el bucle
    source.loop = true;
    
    // Conectar el nodo a la salida del audio
    source.connect(audioContext.destination);
    
    // Iniciar la reproducción
    source.start();
  })
  .catch(error => console.error('Error al cargar el audio:', error));
```

## Explicación
Algunos problemas comunes que pueden surgir al trabajar con `AudioBufferSourceNode` incluyen:

- **Intentar reproducir un nodo después de que se ha detenido**: Una vez que un `AudioBufferSourceNode` ha sido detenido, no se puede iniciar de nuevo. Para reproducir el mismo buffer nuevamente, debes crear un nuevo `AudioBufferSourceNode`.
- **Problemas de carga de audio**: Asegúrate de que la ruta al archivo de audio sea correcta y que el archivo sea accesible en el contexto del navegador. Los navegadores pueden bloquear las solicitudes de recursos de audio si no se cumplen las políticas de CORS.

## Resumen en una línea
El `AudioBufferSourceNode` en JavaScript permite reproducir y manipular audio de alta calidad a través de la API de Web Audio, facilitando la creación de experiencias sonoras enriquecedoras en aplicaciones web.