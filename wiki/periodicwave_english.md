<!--
Meta Description: # PeriodicWave in JavaScript: A Comprehensive Guide for Web Audio API ## Synopsis The `PeriodicWave` interface in JavaScript is part of the Web Audio ...
Meta Keywords: periodicwave, audiocontext, real, audio, harmonics
-->

# PeriodicWave in JavaScript: A Comprehensive Guide for Web Audio API

## Synopsis
The `PeriodicWave` interface in JavaScript is part of the Web Audio API, allowing developers to create complex sound waveforms through custom harmonic content for audio synthesis.

## Documentation
### Purpose
`PeriodicWave` is designed to represent periodic waveforms in audio applications. It is particularly useful for synthesizers that need to generate sounds with specific harmonic profiles, such as musical tones, by defining the amplitude and phase of each harmonic.

### Usage
To create a `PeriodicWave`, you typically use the `AudioContext.createPeriodicWave()` method. This method takes two arrays as input: the first array represents the real part of the wave (the amplitudes of the harmonics), while the second array represents the imaginary part (the phases of the harmonics).

### Syntax
```javascript
let periodicWave = audioContext.createPeriodicWave(real, imag);
```
- `real`: An array of floats representing the amplitudes of the harmonics.
- `imag`: An array of floats representing the phases of the harmonics.

### Parameters
- **`real`**: An array containing the amplitude values for each harmonic. The length of this array dictates the number of harmonics included in the wave.
- **`imag`**: An array containing the phase values for each harmonic. If not specified, a default value of zero is used for all harmonics.

### Properties
Once created, `PeriodicWave` objects can be used with `AudioBufferSourceNode` or `OscillatorNode` to produce sound.

## Examples
### Basic Example
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Define harmonics
let real = new Float32Array([0, 0.5, 0.25]); // Amplitudes for harmonics
let imag = new Float32Array([0, 0, 0]); // Phases for harmonics

// Create a PeriodicWave
let periodicWave = audioContext.createPeriodicWave(real, imag);

// Create an OscillatorNode
let oscillator = audioContext.createOscillator();
oscillator.setPeriodicWave(periodicWave);

// Connect and start
oscillator.connect(audioContext.destination);
oscillator.start();
```

### Custom Harmonic Example
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

let real = new Float32Array([0, 1, 0.5, 0.2]); // Custom amplitudes
let imag = new Float32Array([0, 0, 0, 0]); // Default phases

let periodicWave = audioContext.createPeriodicWave(real, imag);
let oscillator = audioContext.createOscillator();
oscillator.setPeriodicWave(periodicWave);
oscillator.connect(audioContext.destination);
oscillator.start();
```

## Explanation
### Common Pitfalls
- **Understanding Harmonic Content**: When defining the `real` and `imag` arrays, ensure that you understand the harmonic content you wish to create. The first element of the `real` array corresponds to the fundamental frequency, while subsequent elements represent higher harmonics.
  
- **AudioContext State**: If you attempt to create or manipulate audio nodes before the `AudioContext` is in the 'running' state, you may encounter errors. Always ensure that the context is properly started.

- **Array Length**: The lengths of the `real` and `imag` arrays must match. If they do not, the `PeriodicWave` will not be created correctly, leading to unexpected audio outputs.

### Additional Notes
- The Web Audio API is asynchronous; therefore, ensure that the audio context is resumed (if suspended) when playing sounds.
- The `PeriodicWave` object is immutable after creation, meaning you cannot modify its properties once defined.

## One Line Summary
The `PeriodicWave` interface in JavaScript's Web Audio API allows the creation of custom periodic waveforms for advanced audio synthesis.