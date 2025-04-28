<!--
Meta Description: # Understanding AudioScheduledSourceNode in JavaScript: A Comprehensive Guide ## Synopsis The `AudioScheduledSourceNode` is an abstract interface in t...
Meta Keywords: audio, playback, source, audiocontext, audioscheduledsourcenode
-->

# Understanding AudioScheduledSourceNode in JavaScript: A Comprehensive Guide

## Synopsis
The `AudioScheduledSourceNode` is an abstract interface in the Web Audio API, serving as the base for audio sources that can be scheduled to play at specific times. This powerful feature allows developers to create complex audio applications and enhance user experiences in web applications.

## Documentation

### Purpose
`AudioScheduledSourceNode` provides the framework for audio sources that can be controlled in terms of timing. This includes nodes like `AudioBufferSourceNode` and `ConstantSourceNode`, which inherit from `AudioScheduledSourceNode`. It enables developers to schedule audio playback, control when audio starts and stops, and manipulate the timing of sound effects in real-time audio processing.

### Usage
To utilize `AudioScheduledSourceNode`, one typically creates an instance of a derived class and connects it to an audio context. Here's a brief overview of how it works:

1. **Create an Audio Context**: This is the foundation for any audio work in the Web Audio API.
2. **Create a Source Node**: Use a derived class to create an audio source.
3. **Schedule Playback**: Utilize methods like `start()` and `stop()` to control audio timing.
4. **Connect to the Destination**: Finally, connect the source node to the audio context's destination to hear the output.

### Details
- **Inheritance**: `AudioScheduledSourceNode` is an abstract class; it cannot be instantiated directly. It is inherited by `AudioBufferSourceNode` and `ConstantSourceNode`.
- **Properties**:
  - `startTime`: The time when playback starts, specified in seconds.
  - `stopTime`: The time when playback stops, specified in seconds.
- **Methods**:
  - `start(when)`: Schedules the node to start playback at a specified time.
  - `stop(when)`: Schedules the node to stop playback at a specified time.

## Examples

### Basic Usage Example
Here’s a simple example demonstrating how to use `AudioBufferSourceNode`, which is derived from `AudioScheduledSourceNode`:

```javascript
// Create an AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Load an audio file
fetch('path/to/audio/file.mp3')
    .then(response => response.arrayBuffer())
    .then(data => audioContext.decodeAudioData(data))
    .then(buffer => {
        // Create an AudioBufferSourceNode
        const source = audioContext.createBufferSource();
        source.buffer = buffer;

        // Connect to the output
        source.connect(audioContext.destination);

        // Start playback
        source.start(0); // Start immediately
    })
    .catch(error => console.error('Error with decoding audio data', error));
```

### Scheduling Playback Example
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const source = audioContext.createBufferSource();

// Assuming `buffer` is an audio buffer loaded previously
source.buffer = buffer; 
source.connect(audioContext.destination);

// Schedule start at 2 seconds from now
source.start(audioContext.currentTime + 2);
```

## Explanation
When working with `AudioScheduledSourceNode`, developers should be aware of a few common pitfalls:

1. **Context State**: Ensure that the audio context is in a "running" state. If it's "suspended", audio will not play.
2. **Timing Parameters**: When scheduling playback, consider that the `start()` and `stop()` methods accept parameters in seconds relative to the context's current time.
3. **Single Playback**: An `AudioBufferSourceNode` can be played only once. If you need to play the same audio again, you must create a new instance.

## One Line Summary
`AudioScheduledSourceNode` is an abstract interface in the Web Audio API that allows developers to schedule audio playback with precise timing control.