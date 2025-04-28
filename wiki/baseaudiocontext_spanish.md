<!--
Meta Description: # BaseAudioContext: Contexto de Audio en JavaScript ## Sinopsis El `BaseAudioContext` es una interfaz fundamental en la Web Audio API de JavaScript qu...
Meta Keywords: audio, contexto, que, audiocontext, para
-->

# BaseAudioContext: Contexto de Audio en JavaScript

## Sinopsis
El `BaseAudioContext` es una interfaz fundamental en la Web Audio API de JavaScript que proporciona un contexto de audio para la manipulación y procesamiento de audio en aplicaciones web. Permite la creación y control de nodos de audio, facilitando la creación de experiencias sonoras interactivas y dinámicas.

## Documentación
### Propósito
`BaseAudioContext` es la clase base para todos los contextos de audio en la Web Audio API. Esta interfaz permite gestionar el flujo de audio, así como controlar la creación de fuentes de audio, efectos y nodos de destino.

### Uso
Para utilizar `BaseAudioContext`, es común instanciar uno de sus derivados, como `AudioContext`. A través de este contexto, se pueden crear y conectar nodos de audio.

### Detalles
- **Creación**: Un nuevo contexto de audio se puede crear llamando al constructor `AudioContext()` o `OfflineAudioContext()`.
- **Conexión de Nodos**: Los nodos de audio se pueden conectar entre sí utilizando el método `connect()`.
- **Control del Tiempo**: `BaseAudioContext` proporciona métodos para gestionar la temporización de audio, como `currentTime`, que devuelve el tiempo actual del contexto de audio.
- **Manejo de Eventos**: Permite el manejo de eventos como `statechange`, que se dispara cuando el estado del contexto cambia (por ejemplo, al ser suspendido o cerrado).

## Ejemplos
### Ejemplo Básico de Creación de un Contexto de Audio
```javascript
// Crear un nuevo contexto de audio
const audioContext = new AudioContext();

// Verificar el tiempo actual del contexto
console.log(audioContext.currentTime);
```

### Ejemplo de Conexión de Nodos
```javascript
// Crear un contexto de audio
const audioContext = new AudioContext();

// Crear un oscilador
const oscillator = audioContext.createOscillator();

// Conectar el oscilador al destino (altavoces)
oscillator.connect(audioContext.destination);

// Iniciar el oscilador
oscillator.start();
```

## Explicación
### Errores Comunes
- **No Soportado en Todos los Navegadores**: Asegúrate de que el navegador en el que estás trabajando es compatible con la Web Audio API.
- **Contexto Suspendido**: Si intentas reproducir audio sin que el contexto esté en estado "running", puede que no se escuche nada. Usa `audioContext.resume()` para reanudarlo.
- **Uso de `OfflineAudioContext`**: Recuerda que `OfflineAudioContext` se utiliza para procesar audio sin necesidad de reproducción en tiempo real, lo que puede ser útil para pre-renderizar audio.

## Resumen en Una Línea
`BaseAudioContext` es la interfaz base de la Web Audio API en JavaScript que permite crear y gestionar contextos de audio para aplicaciones web interactivas.