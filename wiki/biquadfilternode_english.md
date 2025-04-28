<!--
Meta Description: # BiquadFilterNode: A Comprehensive Guide to Audio Filtering in JavaScript ## Synopsis The `BiquadFilterNode` is a powerful audio processing interface...
Meta Keywords: audio, filter, audiocontext, biquadfilternode, type
-->

# BiquadFilterNode: A Comprehensive Guide to Audio Filtering in JavaScript

## Synopsis
The `BiquadFilterNode` is a powerful audio processing interface in the Web Audio API that allows developers to create versatile filter effects for audio signals, including low-pass, high-pass, band-pass, and more.

## Documentation

### Purpose
The `BiquadFilterNode` is designed to apply a variety of filter types to audio signals in real-time. This node is essential for sound design, allowing developers to shape audio frequencies dynamically.

### Usage
To use the `BiquadFilterNode`, you must first create an `AudioContext` and then call the `createBiquadFilter` method. This node can filter audio signals based on the specified filter type, frequency, and quality factor.

### Properties
- **type**: Specifies the type of filter (e.g., 'lowpass', 'highpass', 'bandpass').
- **frequency**: A `AudioParam` representing the cutoff frequency in hertz.
- **detune**: A `AudioParam` that specifies the tuning detune in cents.
- **Q**: A `AudioParam` that represents the quality factor, influencing the bandwidth of the filter.
- **gain**: A `AudioParam` that adjusts the gain of the filter for certain types (e.g., 'peaking' and 'notch').

### Methods
- **connect(destination)**: Connects the filter node to another audio node.
- **disconnect(destination)**: Disconnects the filter node from another audio node.

### Example
Here is a basic example demonstrating how to create and use a `BiquadFilterNode` in JavaScript:

```javascript
// Create an AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Create an oscillator
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 note

// Create a BiquadFilterNode
const biquadFilter = audioContext.createBiquadFilter();
biquadFilter.type = 'lowpass'; // Set the filter type to low-pass
biquadFilter.frequency.setValueAtTime(300, audioContext.currentTime); // Cutoff frequency

// Connect the nodes
oscillator.connect(biquadFilter);
biquadFilter.connect(audioContext.destination);

// Start the oscillator
oscillator.start();
```

## Explanation
### Common Pitfalls
- **AudioContext State**: Ensure that the `AudioContext` is in the running state before attempting to play audio. Call `audioContext.resume()` if necessary.
- **Filter Configuration**: Always set the filter's properties (like frequency and type) before connecting it to other nodes to avoid unexpected behavior.
- **Browser Compatibility**: Some older browsers may not support the Web Audio API; always check for compatibility.

### Gotchas
- **Real-Time Changes**: Changing filter parameters in real-time can introduce audio artifacts. Use automation or scheduled parameter changes to minimize these issues.
- **Gain Settings**: When using certain filter types that adjust gain, ensure the overall signal does not clip, which can lead to distortion.

## One Line Summary
The `BiquadFilterNode` in JavaScript allows developers to apply various filtering effects to audio signals, enhancing sound design and audio processing capabilities.