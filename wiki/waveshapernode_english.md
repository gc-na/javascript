<!--
Meta Description: # WaveShaperNode in JavaScript: A Comprehensive Guide ## Synopsis The `WaveShaperNode` is a powerful feature in the Web Audio API that allows develope...
Meta Keywords: curve, waveshapernode, audio, audiocontext, const
-->

# WaveShaperNode in JavaScript: A Comprehensive Guide

## Synopsis
The `WaveShaperNode` is a powerful feature in the Web Audio API that allows developers to create custom audio wave shapes, enabling distortion effects and sound manipulation in web applications.

## Documentation
### Purpose
The `WaveShaperNode` is used for audio signal processing, specifically for shaping the waveform of an audio signal. This node allows developers to define a custom curve that determines how the audio signal will be modified, making it ideal for creating unique sound effects, such as distortion and saturation.

### Usage
To utilize a `WaveShaperNode`, you need to first create an `AudioContext`. You can then create a `WaveShaperNode` instance using the `createWaveShaper()` method of the `AudioContext`. The key property of the `WaveShaperNode` is its `curve`, which is an array that defines the mapping of input values to output values.

```javascript
// Create an audio context
const audioContext = new AudioContext();

// Create a WaveShaperNode
const waveShaperNode = audioContext.createWaveShaper();

// Define a curve
const curve = new Float32Array(44100);
for (let i = 0; i < curve.length; ++i) {
    const x = (i / 44100) * 2 - 1; // Normalize input to -1 to 1
    curve[i] = (x < 0) ? Math.pow(x, 2) : Math.pow(x, 0.5); // Example shaping
}

// Assign the curve to the wave shaper
waveShaperNode.curve = curve;

// Connect the nodes (e.g., oscillator to wave shaper to destination)
const oscillator = audioContext.createOscillator();
oscillator.connect(waveShaperNode);
waveShaperNode.connect(audioContext.destination);
oscillator.start();
```

### Properties and Methods
- **curve**: A `Float32Array` that defines the curve used to modify the audio signal.
- **oversample**: A string that specifies how the wave shaping is performed. Options are "none", "2x", or "4x".
  
### Example Usage
Here’s a simple example demonstrating how to create a distortion effect using the `WaveShaperNode`.

```javascript
function createDistortion(audioContext) {
    const waveShaper = audioContext.createWaveShaper();

    // Create a curve for distortion
    const curve = new Float32Array(44100);
    for (let i = 0; i < curve.length; i++) {
        const x = (i / 44100) * 2 - 1; // Normalize input
        curve[i] = (Math.abs(x) < 0.5) ? x : (x < 0 ? -1 : 1); // Hard clipping
    }
    waveShaper.curve = curve;

    return waveShaper;
}

const audioCtx = new AudioContext();
const distortionNode = createDistortion(audioCtx);
const oscillator = audioCtx.createOscillator();

oscillator.connect(distortionNode);
distortionNode.connect(audioCtx.destination);
oscillator.start();
```

## Explanation
### Common Pitfalls
- **Curve Definition**: The curve must be carefully defined. If the specified `curve` is not normalized between -1 to 1, it can result in unexpected audio output.
- **AudioContext State**: Ensure that the `AudioContext` is in a running state before attempting to play audio. You may need to handle user gestures to start playback due to browser autoplay policies.
- **Oversampling**: While oversampling can improve sound quality, it can also increase CPU usage. Use it judiciously based on your application needs.

### Additional Notes
- The `WaveShaperNode` can be used in conjunction with other audio nodes (e.g., gain, filter) to achieve more complex audio processing.
- The node is particularly useful in music applications where unique sound signatures are desired.

## One Line Summary
The `WaveShaperNode` in JavaScript's Web Audio API enables custom waveform shaping for creating unique audio effects, particularly distortion.