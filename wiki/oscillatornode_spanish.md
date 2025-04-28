<!--
Meta Description: # OscillatorNode en JavaScript: Todo lo que Necesitas Saber ## Sinopsis El `OscillatorNode` es una interfaz del Web Audio API en JavaScript que permit...
Meta Keywords: audiocontext, oscillator, javascript, oscillatornode, que
-->

# OscillatorNode en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
El `OscillatorNode` es una interfaz del Web Audio API en JavaScript que permite generar ondas sonoras de diferentes formas y frecuencias, siendo fundamental para la creación de sonidos en aplicaciones web.

## Documentación
El `OscillatorNode` se utiliza dentro del contexto de un `AudioContext` para crear y controlar osciladores de audio. Esta interfaz permite generar señales de audio de diferentes formas de onda, incluyendo seno, cuadrada, triangular y de ruido.

### Propósito
El propósito del `OscillatorNode` es facilitar la síntesis de sonido mediante la generación de ondas periódicas, que pueden ser utilizadas en música, efectos de sonido y aplicaciones interactivas.

### Uso
Para utilizar un `OscillatorNode`, sigue los pasos a continuación:

1. **Crear un AudioContext**:
   ```javascript
   const audioContext = new AudioContext();
   ```

2. **Crear un OscillatorNode**:
   ```javascript
   const oscillator = audioContext.createOscillator();
   ```

3. **Configurar propiedades del oscilador**:
   - **Tipo de onda**: Puede ser `'sine'`, `'square'`, `'sawtooth'`, o `'triangle'`.
   - **Frecuencia**: Se establece en hercios (Hz).
   ```javascript
   oscillator.type = 'sine'; // Tipo de onda
   oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // Frecuencia de 440 Hz (La)
   ```

4. **Conectar el oscilador al destino**:
   ```javascript
   oscillator.connect(audioContext.destination);
   ```

5. **Iniciar y detener el oscilador**:
   ```javascript
   oscillator.start(); // Inicia el oscilador
   oscillator.stop(audioContext.currentTime + 2); // Detiene el oscilador después de 2 segundos
   ```

## Ejemplos
### Ejemplo Básico de un OscillatorNode
```javascript
const audioContext = new AudioContext();
const oscillator = audioContext.createOscillator();

oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime);
oscillator.connect(audioContext.destination);
oscillator.start();
oscillator.stop(audioContext.currentTime + 2);
```

### Ejemplo de Diferentes Tipos de Onda
```javascript
const audioContext = new AudioContext();

const playOscillator = (type) => {
    const oscillator = audioContext.createOscillator();
    oscillator.type = type;
    oscillator.frequency.setValueAtTime(440, audioContext.currentTime);
    oscillator.connect(audioContext.destination);
    oscillator.start();
    oscillator.stop(audioContext.currentTime + 1);
};

// Ejecutar diferentes tipos de ondas
['sine', 'square', 'sawtooth', 'triangle'].forEach(type => playOscillator(type));
```

## Explicación
### Errores Comunes
- **No iniciar el AudioContext**: Asegúrate de que el `AudioContext` se haya iniciado, ya que algunos navegadores requieren una interacción del usuario (como un clic) para permitir la reproducción de audio.
- **Frecuencia fuera de rango**: Las frecuencias deben estar en un rango audible (20 Hz a 20 kHz) para ser escuchadas; frecuencias fuera de este rango pueden resultar en sonidos inaudibles.
- **Detener el oscilador**: Recuerda detener el oscilador después de haberlo iniciado para evitar que continúe sonando indefinidamente.

### Notas Adicionales
- El `OscillatorNode` tiene un método `setPeriodicWave` que permite usar formas de onda personalizadas.
- La frecuencia y el tipo de onda se pueden cambiar en tiempo real, lo que permite crear efectos dinámicos.

## Resumen en una Línea
El `OscillatorNode` es una herramienta esencial en JavaScript para generar sonidos mediante ondas sonoras de diferentes tipos y frecuencias en aplicaciones web.