<!--
Meta Description: # PannerNode: A Comprehensive Guide to 3D Audio in JavaScript ## Synopsis The `PannerNode` is a part of the Web Audio API in JavaScript that enables d...
Meta Keywords: audio, pannernode, position, create, source
-->

# PannerNode: A Comprehensive Guide to 3D Audio in JavaScript

## Synopsis
The `PannerNode` is a part of the Web Audio API in JavaScript that enables developers to create a three-dimensional audio experience by simulating sound sources in a 3D space.

## Documentation
### Overview
The `PannerNode` allows for the positioning of audio sources in three-dimensional space, enabling developers to create immersive audio environments. It provides properties and methods to manipulate sound characteristics based on the listener's position and orientation.

### Purpose
The primary purpose of the `PannerNode` is to simulate spatial audio effects in web applications, enhancing user experience in games, virtual reality, and other interactive audio applications.

### Usage
To use a `PannerNode`, you must first create an instance of the Web Audio API's `AudioContext`. You can then create a `PannerNode` and connect it to an audio source and the destination (usually the speakers).

### Key Properties
- **panningModel**: Defines the panning algorithm to use (e.g., 'equalpower', 'HRTF').
- **distanceModel**: Specifies the model for distance attenuation (e.g., 'linear', 'exponential').
- **refDistance**: The reference distance, where the audio is at its original volume.
- **maxDistance**: The maximum distance at which the audio can be heard.
- **rolloffFactor**: A factor that determines how quickly the sound fades over distance.
- **position**: A 3D vector indicating the position of the sound source.
- **orientation**: A 3D vector indicating the direction the sound source is facing.

### Methods
- **setPosition(x, y, z)**: Sets the position of the sound source.
- **setOrientation(x, y, z)**: Sets the orientation of the sound source.

### Example
Here’s a simple example of how to create a `PannerNode` and use it to position audio in 3D space:

```javascript
// Create an AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Create a PannerNode
const panner = audioContext.createPanner();
panner.panningModel = 'HRTF';
panner.distanceModel = 'linear';
panner.refDistance = 1;
panner.maxDistance = 100;
panner.rolloffFactor = 1;

// Set the position of the PannerNode
panner.setPosition(0, 0, -5); // Position 5 units in front of the listener

// Create an audio source
const audioElement = new Audio('path/to/audio.mp3');
const source = audioContext.createMediaElementSource(audioElement);

// Connect the source to the PannerNode and the PannerNode to the destination
source.connect(panner);
panner.connect(audioContext.destination);

// Start playing the audio
audioElement.play();
```

## Explanation
### Common Pitfalls
1. **Audio Context State**: Ensure that the `AudioContext` is in the 'running' state before playing audio. It may be in the 'suspended' state depending on browser policies.
2. **Positioning**: If the position of the `PannerNode` is not set correctly, the spatial audio effects may not be perceived correctly by the listener.
3. **Browser Support**: Not all browsers may support specific features of the `PannerNode`, so it's essential to test across different platforms.

### Gotchas
- The `PannerNode` is sensitive to the listener's position as well. You might want to adjust the listener's position and orientation to see the effect of the `PannerNode` accurately.
- If using multiple `PannerNodes`, consider how they interact, as overlapping sounds may create complex audio scenarios.

## One Line Summary
The `PannerNode` in JavaScript's Web Audio API enables the creation of immersive 3D audio experiences by simulating the spatial positioning of sound sources.