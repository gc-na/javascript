<!--
Meta Description: # DelayNode en JavaScript: Control de Audio en Tiempo Real ## Sinopsis DelayNode es una interfaz de la API Web Audio de JavaScript que permite crear u...
Meta Keywords: delaynode, audio, tiempo, retardo, que
-->

# DelayNode en JavaScript: Control de Audio en Tiempo Real

## Sinopsis
DelayNode es una interfaz de la API Web Audio de JavaScript que permite crear un efecto de retardo en el audio, ofreciendo la capacidad de retrasar la reproducción de una señal de audio en un tiempo específico.

## Documentación
### Propósito
DelayNode se utiliza para aplicar un retraso a la señal de audio, lo que permite crear efectos de eco y mejora de la experiencia auditiva. Es especialmente útil en aplicaciones de música y juegos que requieren manipulación de audio en tiempo real.

### Uso
Para crear un DelayNode, es necesario tener acceso a un contexto de audio. A continuación se detallan los pasos básicos:

1. **Crear un contexto de audio**: Inicia un nuevo AudioContext.
2. **Crear el DelayNode**: Usar el método `createDelay()` del contexto de audio.
3. **Conectar nodos**: Conectar el DelayNode a otras fuentes de audio y a la salida del contexto de audio.

### Detalles
El DelayNode se puede configurar con dos parámetros principales:
- **maxDelayTime**: Representa el tiempo máximo de retardo en segundos que puede ser aplicado.
- **delayTime**: Un parámetro que se puede ajustar en tiempo real para modificar el tiempo de retardo.

## Ejemplos
### Ejemplo Básico de DelayNode
```javascript
// Crear un contexto de audio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Crear un DelayNode
const delayNode = audioContext.createDelay(5.0); // 5 segundos máximo de retardo

// Crear una fuente de audio (por ejemplo, un oscilador)
const oscillator = audioContext.createOscillator();
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // Frecuencia de 440 Hz

// Conectar el oscilador al DelayNode
oscillator.connect(delayNode);

// Conectar el DelayNode a la salida del contexto de audio
delayNode.connect(audioContext.destination);

// Iniciar el oscilador
oscillator.start();
```

### Ajustar el Tiempo de Retardo
```javascript
// Ajustar el tiempo de retardo a 1 segundo
delayNode.delayTime.setValueAtTime(1.0, audioContext.currentTime);
```

## Explicación
Es importante tener en cuenta que el uso de DelayNode puede introducir latencia en la señal de audio, especialmente si se establece un tiempo de retardo muy alto. Además, el uso excesivo de efectos de retardo puede causar distorsión si no se gestiona adecuadamente. Al conectar múltiples nodos, asegúrate de que la ruta de señal no se vuelva demasiado compleja, ya que puede afectar el rendimiento.

## Resumen en Una Frase
DelayNode es una herramienta poderosa en JavaScript para agregar efectos de retardo a las señales de audio, mejorando la experiencia auditiva en aplicaciones interactivas.