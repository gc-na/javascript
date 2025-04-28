<!--
Meta Description: # DelayNode in JavaScript: Mastering Audio Delay Effects ## Synopsis The `DelayNode` is a part of the Web Audio API in JavaScript that allows develope...
Meta Keywords: delaynode, delay, audiocontext, audio, oscillator
-->

# DelayNode in JavaScript: Mastering Audio Delay Effects

## Synopsis
The `DelayNode` is a part of the Web Audio API in JavaScript that allows developers to create audio delay effects in web applications, enhancing sound design by manipulating audio playback timing.

## Documentation
### Purpose
The `DelayNode` is designed to delay the audio signal passing through it by a specified duration, creating various audio effects such as echoes or reverberations. It is especially useful in music production, game audio, and interactive applications where timing is critical.

### Usage
To utilize a `DelayNode`, you must first create an `AudioContext`. Once the context is established, you can instantiate a `DelayNode` with desired parameters, such as delay time and feedback.

#### Creating a DelayNode
```javascript
const audioContext = new AudioContext();
const delayNode = audioContext.createDelay();
```

#### Parameters
- **maxDelayTime (optional)**: The maximum delay time in seconds. This defines the longest delay that the node can apply. The default value is 1.0 seconds.
- **delayTime**: A property of the `DelayNode` that represents the time delay in seconds. This value can be set and changed dynamically during playback.

### Connecting Nodes
To use the `DelayNode`, connect it to other audio nodes (like `OscillatorNode`, `GainNode`, etc.):

```javascript
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // Frequency in Hz

// Connect the oscillator to the delay node
oscillator.connect(delayNode);
delayNode.connect(audioContext.destination);

// Start the oscillator
oscillator.start();
```

## Examples
### Basic Delay Effect
Here’s a simple example demonstrating the use of a `DelayNode` to create a basic echo effect:

```javascript
const audioContext = new AudioContext();
const delayNode = audioContext.createDelay();
delayNode.delayTime.value = 0.5; // 500 milliseconds delay

const oscillator = audioContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime);

oscillator.connect(delayNode);
delayNode.connect(audioContext.destination);

oscillator.start();
```

### Adjustable Delay Time
You can dynamically adjust the delay time during playback:

```javascript
delayNode.delayTime.setValueAtTime(0.5, audioContext.currentTime); // Set initial delay
setTimeout(() => {
    delayNode.delayTime.setValueAtTime(1.0, audioContext.currentTime); // Change delay after 2 seconds
}, 2000);
```

## Explanation
### Common Pitfalls
- **AudioContext State**: Ensure the `AudioContext` is in the "running" state before trying to play audio. If the context is suspended, you need to resume it.
- **Delay Time Range**: The delay time must be within the range defined by `maxDelayTime`. Attempting to set a delay time beyond this limit will cause an error.
- **Browser Compatibility**: Always check for compatibility with the Web Audio API, as not all browsers may support every feature.

### Gotchas
- **Node Connections**: Ensure that the nodes are correctly connected in the audio graph; otherwise, no sound will be produced.
- **Latency Issues**: Be mindful of latency introduced by the delay effect, especially in real-time applications like games.

## One Line Summary
The `DelayNode` in JavaScript's Web Audio API enables the creation of sophisticated audio delay effects, enhancing interactive audio experiences.