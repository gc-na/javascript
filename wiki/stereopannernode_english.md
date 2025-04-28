<!--
Meta Description: # StereoPannerNode in JavaScript: A Comprehensive Guide to 3D Audio Panning ## Synopsis The `StereoPannerNode` is a powerful feature in the Web Audio ...
Meta Keywords: audio, pan, value, stereopannernode, audiocontext
-->

# StereoPannerNode in JavaScript: A Comprehensive Guide to 3D Audio Panning

## Synopsis
The `StereoPannerNode` is a powerful feature in the Web Audio API that allows developers to control the spatial positioning of audio sources in a stereo field, enabling a more immersive audio experience on the web.

## Documentation

### Purpose
The `StereoPannerNode` is designed to create a stereo sound panning effect, allowing you to position audio sources between the left and right speakers. This is particularly useful for creating realistic audio environments in web applications, games, and interactive experiences.

### Usage
To use the `StereoPannerNode`, you need to have access to the Web Audio API through the `AudioContext`. Here’s how to create and configure a `StereoPannerNode`:

1. **Create an Audio Context**: This is the main interface for managing and directing audio.
2. **Create the StereoPannerNode**: Use the `createStereoPanner` method of the `AudioContext`.
3. **Set the pan value**: The pan value ranges from -1 (full left) to 1 (full right), with 0 being centered.
4. **Connect the node**: Connect the `StereoPannerNode` to the audio source and the destination.

#### Example Code

```javascript
// Step 1: Create an Audio Context
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Step 2: Create a StereoPannerNode
const panner = audioContext.createStereoPanner();

// Step 3: Set the pan value (range: -1 to 1)
panner.pan.value = -1; // Full left

// Step 4: Create an audio source (e.g., an oscillator)
const oscillator = audioContext.createOscillator();
oscillator.frequency.value = 440; // A4 note

// Step 5: Connect the audio nodes
oscillator.connect(panner);
panner.connect(audioContext.destination);

// Step 6: Start the oscillator
oscillator.start();
```

## Examples

### Example 1: Basic Left Pan
```javascript
panner.pan.value = -1; // Full left
```

### Example 2: Basic Right Pan
```javascript
panner.pan.value = 1; // Full right
```

### Example 3: Center Pan
```javascript
panner.pan.value = 0; // Center
```

### Example 4: Dynamic Panning
```javascript
panner.pan.setValueAtTime(0.5, audioContext.currentTime); // Move to the right
panner.pan.linearRampToValueAtTime(-0.5, audioContext.currentTime + 2); // Move left over 2 seconds
```

## Explanation
### Common Pitfalls
1. **Volume Levels**: Users often overlook adjusting the volume or gain, leading to unexpected audio levels. Ensure that the audio source is adequately set up.
2. **Pan Value Range**: The pan value must be between -1 and 1. Values outside this range will not produce expected results and may lead to audio distortion or silence.
3. **Audio Context State**: The `AudioContext` must be in a running state to play audio. This may require user interaction (like a button click) in some browsers due to autoplay restrictions.

### Gotchas
- Some browsers may require user interaction (like a click) to start audio playback.
- The `StereoPannerNode` does not perform any audio processing until it is connected to a destination node.
- Dynamic changes to the pan value may not immediately reflect in audio playback without proper timing management.

## One Line Summary
The `StereoPannerNode` in JavaScript's Web Audio API allows developers to create immersive audio experiences by controlling the stereo positioning of sound sources.