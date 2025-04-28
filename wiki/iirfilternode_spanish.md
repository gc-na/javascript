<!--
Meta Description: # IIRFilterNode: Filtrado Digital en JavaScript ## Sinopsis El `IIRFilterNode` es un nodo de procesamiento de audio en la Web Audio API de JavaScript ...
Meta Keywords: iirfilternode, los, audio, que, audiocontext
-->

# IIRFilterNode: Filtrado Digital en JavaScript

## Sinopsis
El `IIRFilterNode` es un nodo de procesamiento de audio en la Web Audio API de JavaScript que permite aplicar un filtro digital de respuesta infinita (IIR) a una señal de audio. Este nodo es esencial para realizar manipulación avanzada de audio, como ecualización y efectos de sonido.

## Documentación
### Propósito
El `IIRFilterNode` se utiliza para aplicar filtros IIR a las señales de audio en tiempo real. A diferencia de los filtros FIR, los filtros IIR pueden tener una respuesta más compleja y requieren menos recursos, lo que los hace ideales para aplicaciones de audio en tiempo real.

### Uso
Para crear un `IIRFilterNode`, se utiliza el método `createIIRFilter()` del `AudioContext`. Este método toma dos matrices: una para los coeficientes de feedforward y otra para los coeficientes de feedback.

#### Sintaxis
```javascript
const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);
```

#### Parámetros
- `feedforward`: Un array de números que contiene los coeficientes de feedforward del filtro.
- `feedback`: Un array de números que contiene los coeficientes de feedback del filtro.

### Ejemplo
Aquí tienes un ejemplo básico de cómo crear y utilizar un `IIRFilterNode` en una aplicación de audio:

```javascript
// Crear un contexto de audio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Coeficientes del filtro
const feedforward = [1, -1.5, 0.7];
const feedback = [1, -0.5];

// Crear el nodo IIRFilter
const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);

// Crear una fuente de sonido
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime);

// Conectar el oscilador al filtro IIR y el filtro al destino
oscillator.connect(iirFilterNode);
iirFilterNode.connect(audioContext.destination);

// Iniciar el oscilador
oscillator.start();
```

## Explicación
Al utilizar `IIRFilterNode`, es importante considerar los siguientes puntos:

- **Coeficientes**: Los coeficientes de feedforward y feedback deben ser elegidos cuidadosamente. Un mal ajuste puede resultar en un comportamiento inesperado del filtro.
- **Rendimiento**: Los filtros IIR son más eficientes en términos de recursos que los filtros FIR, pero pueden introducir inestabilidad si no se configuran correctamente.
- **Compatibilidad**: Asegúrate de que el navegador que estás utilizando soporte la Web Audio API y el nodo `IIRFilterNode`, ya que no todos los navegadores lo implementan de la misma manera.

## Resumen en una línea
El `IIRFilterNode` de JavaScript permite aplicar filtros digitales de respuesta infinita a señales de audio en tiempo real, mejorando la manipulación del sonido en aplicaciones web.