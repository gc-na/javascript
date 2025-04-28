<!--
Meta Description: # AudioNode en JavaScript: Comprendiendo la Interfaz de Audio en la Web ## Sinopsis AudioNode es una interfaz fundamental en la API de Audio de Web, q...
Meta Keywords: audiocontext, audio, oscillator, que, gainnode
-->

# AudioNode en JavaScript: Comprendiendo la Interfaz de Audio en la Web

## Sinopsis
AudioNode es una interfaz fundamental en la API de Audio de Web, que permite la manipulación de audio en aplicaciones web. Esta interfaz se utiliza para crear, conectar y controlar el procesamiento de audio en tiempo real.

## Documentación
### Propósito
AudioNode es un componente clave en la cadena de procesamiento de audio. Representa un nodo en un grafo de audio que puede ser utilizado para generar, modificar o controlar el sonido. Todos los nodos de audio deben ser conectados entre sí para crear un flujo de audio, lo que permite manipular el audio de manera efectiva.

### Uso
Los nodos de audio se crean a través de la interfaz `AudioContext`, la cual actúa como un entorno para el procesamiento de sonido. Existen diferentes tipos de nodos como `GainNode`, `OscillatorNode` y `MediaElementAudioSourceNode`, cada uno con propósitos específicos.

**Creación de un AudioContext:**
```javascript
const audioContext = new AudioContext();
```

**Creación de un OscillatorNode:**
```javascript
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine'; // Tipo de onda
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // Frecuencia en Hertz
oscillator.start();
```

**Conexión de nodos:**
```javascript
oscillator.connect(audioContext.destination);
```

### Detalles
- **Propiedades**: Los AudioNodes pueden tener diferentes propiedades dependiendo de su tipo. Por ejemplo, `GainNode` tiene un método `gain` que permite ajustar el volumen.
- **Conexión**: Los nodos se conectan entre sí usando el método `connect()`, y se desconectan con `disconnect()`.
- **Tipos de AudioNode**:
  - `GainNode`: Controla el volumen.
  - `DelayNode`: Introduce un retraso en el audio.
  - `DynamicsCompressorNode`: Comprime el rango dinámico del audio.

## Ejemplos
### Ejemplo 1: Generar un tono
```javascript
const audioContext = new AudioContext();
const oscillator = audioContext.createOscillator();
oscillator.type = 'square';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime);
oscillator.connect(audioContext.destination);
oscillator.start();
```

### Ejemplo 2: Ajustar el volumen con GainNode
```javascript
const audioContext = new AudioContext();
const oscillator = audioContext.createOscillator();
const gainNode = audioContext.createGain();

oscillator.connect(gainNode);
gainNode.connect(audioContext.destination);
gainNode.gain.setValueAtTime(0.5, audioContext.currentTime); // Ajuste de volumen
oscillator.start();
```

## Explicación
Un error común al trabajar con AudioNode es olvidar que todos los nodos deben ser conectados a un `AudioContext` activo. Asegúrate de que el contexto de audio esté en un estado adecuado (por ejemplo, no en pausa) antes de realizar conexiones. Además, ten en cuenta que algunos navegadores requieren que la interacción del usuario inicie el contexto de audio, por lo que es recomendable asociar el inicio del contexto a un evento como un clic.

## Resumen en una línea
AudioNode es la interfaz fundamental para manipular el audio en aplicaciones web usando la API de Audio de JavaScript.