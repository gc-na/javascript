<!--
Meta Description: # PeriodicWave en JavaScript: Generación de Ondas Periódicas en la Web ## Sinopsis PeriodicWave es una interfaz de la API de Web Audio en JavaScript q...
Meta Keywords: que, periodicwave, audio, onda, web
-->

# PeriodicWave en JavaScript: Generación de Ondas Periódicas en la Web

## Sinopsis
PeriodicWave es una interfaz de la API de Web Audio en JavaScript que permite la creación de ondas periódicas personalizadas, facilitando la generación de sonidos armónicos y complejos en aplicaciones web.

## Documentación
### Propósito
La interfaz PeriodicWave se utiliza para representar una onda periódica en la API de Web Audio. Esto es especialmente útil para sintetizar sonidos de manera precisa, ya que permite a los desarrolladores definir formas de onda complejas a partir de componentes armónicos.

### Uso
Para utilizar PeriodicWave, primero debes tener un contexto de audio creado mediante `AudioContext`. Luego, puedes crear una instancia de PeriodicWave utilizando el método `createPeriodicWave`. Este método acepta dos parámetros: un array de amplitudes y un array de fases, que definen la forma de la onda.

### Detalles
- **Constructor**: `PeriodicWave(context, options)`
  - **context**: Un objeto `AudioContext` que representa el contexto de audio.
  - **options**: Un objeto que puede contener propiedades como `real` y `imaginary`, que son arrays que describen la onda.
  
- **Métodos**:
  - `createPeriodicWave(real, imaginary)`: Crea una nueva onda periódica con las amplitudes y fases especificadas.
  
- **Propiedades**:
  - `real`: Un array que define las amplitudes de los componentes armónicos.
  - `imaginary`: Un array que define las fases de los componentes armónicos.

## Ejemplos
### Ejemplo básico de uso de PeriodicWave
```javascript
// Crear un contexto de audio
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

// Definir amplitudes y fases
const real = new Float32Array([0, 1, 0.5]);
const imaginary = new Float32Array([0, 0, 0]);

// Crear una onda periódica
const periodicWave = audioCtx.createPeriodicWave(real, imaginary);

// Crear un oscilador y asignar la onda periódica
const oscillator = audioCtx.createOscillator();
oscillator.setPeriodicWave(periodicWave);

// Conectar el oscilador al destino y reproducir
oscillator.connect(audioCtx.destination);
oscillator.start();
```

## Explicación
### Errores comunes y notas
- **Dimensiones de los arrays**: Asegúrate de que los arrays `real` e `imaginary` tengan la misma longitud. De lo contrario, se lanzará un error.
- **Contexto de audio**: La llamada a `createPeriodicWave` debe hacerse después de que el contexto de audio esté en un estado activo. Si intentas crear la onda antes de que el contexto esté en ejecución, no funcionará correctamente.
- **Compatibilidad**: Verifica la compatibilidad del navegador con la API de Web Audio, ya que no todos los navegadores pueden soportar esta funcionalidad.

## Resumen en una línea
PeriodicWave es una interfaz de la API de Web Audio en JavaScript que permite crear ondas periódicas personalizadas para la síntesis de sonido en aplicaciones web.