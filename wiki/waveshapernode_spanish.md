<!--
Meta Description: # WaveShaperNode en JavaScript: Guía Completa ## Sinopsis El `WaveShaperNode` es una interfaz de la API Web Audio de JavaScript que permite modificar ...
Meta Keywords: waveshapernode, audio, que, distorsión, una
-->

# WaveShaperNode en JavaScript: Guía Completa

## Sinopsis
El `WaveShaperNode` es una interfaz de la API Web Audio de JavaScript que permite modificar la forma de onda de una señal de audio, añadiendo distorsión y efectos únicos a la producción sonora.

## Documentación
El `WaveShaperNode` forma parte de la API Web Audio, que proporciona herramientas para la manipulación de audio en el navegador. Este nodo permite aplicar una curva de distorsión a una señal de audio, lo que resulta en la modificación de su forma de onda. El `WaveShaperNode` se utiliza comúnmente para crear efectos de distorsión, overdrive y fuzz en audio digital.

### Propósito
El propósito principal del `WaveShaperNode` es alterar la amplitud de una señal de audio en función de la forma de onda definida en su propiedad `curve`. Esta curva puede ser una función de mapeo que determina cómo se transforman las amplitudes de entrada a salidas.

### Uso
Para utilizar un `WaveShaperNode`, sigue estos pasos básicos:

1. Crea un contexto de audio.
2. Crea un `WaveShaperNode`.
3. Establece la curva de distorsión mediante la propiedad `curve`.
4. Conecta el nodo a la cadena de audio.

### Detalles
El `WaveShaperNode` tiene las siguientes propiedades y métodos clave:

- **Curve**: Un `Float32Array` que define la curva de distorsión. Esta curva determina cómo se transforma la señal de entrada.
- **Oversample**: Una propiedad opcional que puede ser `none`, `2x` o `4x`, que indica el método de sobremuestreo usado para suavizar la distorsión.

## Ejemplos

### Ejemplo Básico de Uso
```javascript
// Crear un contexto de audio
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Crear un oscilador
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine'; // Tipo de onda: seno
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // Frecuencia en Hz

// Crear un WaveShaperNode
const waveShaper = audioContext.createWaveShaper();

// Definir la curva de distorsión
const curve = new Float32Array(256);
for (let i = 0; i < 256; ++i) {
    const x = (i * 2) / 256 - 1; // Normalizar a rango [-1, 1]
    curve[i] = (Math.abs(x) < 0.5) ? x * 2 : (x < 0 ? -1 : 1); // Curva de distorsión
}
waveShaper.curve = curve;

// Conectar los nodos
oscillator.connect(waveShaper);
waveShaper.connect(audioContext.destination);

// Iniciar el oscilador
oscillator.start();
```

### Ejemplo de Sobremuestreo
```javascript
// Crear un WaveShaperNode con sobremuestreo
const waveShaperWithOversample = audioContext.createWaveShaper();
waveShaperWithOversample.oversample = '4x'; // Usar 4x de sobremuestreo

// Definir la curva de distorsión como en el ejemplo anterior
waveShaperWithOversample.curve = curve;

// Conectar los nodos
oscillator.connect(waveShaperWithOversample);
waveShaperWithOversample.connect(audioContext.destination);
```

## Explicación
Al trabajar con `WaveShaperNode`, es importante tener en cuenta:

- **Curvas Complejas**: Si bien puedes crear curvas simples, las formas de onda más complejas pueden resultar en efectos sonoros interesantes, pero también pueden introducir artefactos si no se configuran correctamente.
- **Rango de Amplitud**: Asegúrate de que los valores en la curva estén en el rango de -1 a 1, ya que valores fuera de este rango pueden producir distorsiones inesperadas.
- **Sobremuestreo**: Utilizar sobremuestreo puede mejorar la calidad del sonido, pero también aumentará el uso de recursos, lo que puede ser un factor a considerar en dispositivos más limitados.

## Resumen en Una Línea
El `WaveShaperNode` en JavaScript es una herramienta poderosa para modificar la forma de onda de señales de audio, permitiendo la creación de efectos de distorsión únicos en la producción musical.