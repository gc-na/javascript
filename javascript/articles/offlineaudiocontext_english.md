<!--
Meta Description: # OfflineAudioContext in JavaScript: A Comprehensive Guide ## Synopsis `OfflineAudioContext` is a powerful feature in the Web Audio API that allows de...
Meta Keywords: audio, offlinecontext, offlineaudiocontext, oscillator, length
-->

# OfflineAudioContext in JavaScript: A Comprehensive Guide

## Synopsis
`OfflineAudioContext` is a powerful feature in the Web Audio API that allows developers to render audio processing offline, enabling high-quality audio synthesis and manipulation without the need for real-time playback.

## Documentation
### Purpose
`OfflineAudioContext` is designed to create audio processing nodes that can be rendered without the need for immediate output. This feature is particularly useful for generating audio files, applying effects, or performing complex audio operations without affecting real-time performance.

### Usage
To use `OfflineAudioContext`, follow these steps:

1. **Instantiate the OfflineAudioContext**: Create an instance by specifying the number of channels, the length of the audio buffer in sample frames, and the sample rate.

   ```javascript
   const offlineContext = new OfflineAudioContext(numberOfChannels, length, sampleRate);
   ```

2. **Create Audio Nodes**: Generate audio nodes (like `GainNode`, `OscillatorNode`, etc.) as you would in a regular `AudioContext`.

3. **Connect Nodes**: Connect the created nodes to the `OfflineAudioContext`.

4. **Start Rendering**: Call the `startRendering()` method, which returns a promise that resolves with the rendered audio buffer.

   ```javascript
   offlineContext.startRendering().then((renderedBuffer) => {
       // Do something with the rendered audio buffer
   });
   ```

### Details
- **Constructor Parameters**:
  - `numberOfChannels`: An integer representing the number of channels (1 for mono, 2 for stereo, etc.).
  - `length`: The length of the audio in sample frames, defining how long the audio will be.
  - `sampleRate`: The sample rate in Hz (e.g., 44100 for CD quality).

- **Methods**:
  - `startRendering()`: Begins the rendering process, returning a promise that resolves with an `AudioBuffer`.
  
- **Properties**:
  - `length`: The length of the audio buffer.
  - `sampleRate`: The sample rate used for the audio context.

## Examples
### Basic Example
Here's a simple example of using `OfflineAudioContext` to create a sine wave oscillator:

```javascript
const offlineContext = new OfflineAudioContext(1, 44100 * 2, 44100); // 1 channel, 2 seconds, 44.1kHz

const oscillator = offlineContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, offlineContext.currentTime); // A4 note
oscillator.connect(offlineContext.destination);
oscillator.start();
oscillator.stop(offlineContext.currentTime + 2); // Stop after 2 seconds

offlineContext.startRendering().then((renderedBuffer) => {
    console.log('Rendering complete', renderedBuffer);
});
```

### Advanced Example
Rendering audio with effects applied:

```javascript
const offlineContext = new OfflineAudioContext(2, 44100 * 3, 44100); // 2 channels, 3 seconds, 44.1kHz
const gainNode = offlineContext.createGain();
gainNode.gain.setValueAtTime(0.5, offlineContext.currentTime); // Reduce volume

const oscillator = offlineContext.createOscillator();
oscillator.type = 'square';
oscillator.frequency.setValueAtTime(440, offlineContext.currentTime); // A4 note

oscillator.connect(gainNode);
gainNode.connect(offlineContext.destination);
oscillator.start();
oscillator.stop(offlineContext.currentTime + 3); // Stop after 3 seconds

offlineContext.startRendering().then((renderedBuffer) => {
    console.log('Rendered audio with gain effect', renderedBuffer);
});
```

## Explanation
### Common Pitfalls
- **Not Handling Promises**: Forgetting to handle the promise returned by `startRendering()` can lead to unhandled rejections. Always use `.then()` or `async/await` to manage the results.
  
- **Output Limitations**: The `length` parameter must be carefully set. If it's too long, it may lead to performance issues or browser limitations.

- **Audio Context State**: Ensure that the `OfflineAudioContext` is not in a 'closed' state when attempting to render audio. 

### Additional Notes
- `OfflineAudioContext` is particularly useful for generating audio files for playback later, such as in game audio or web applications that require high-quality audio synthesis.

- While `OfflineAudioContext` can handle complex audio processing, it may not support all real-time capabilities found in a regular `AudioContext`.

## One Line Summary
`OfflineAudioContext` allows developers to perform audio rendering offline, enabling high-quality audio synthesis and processing without real-time constraints.