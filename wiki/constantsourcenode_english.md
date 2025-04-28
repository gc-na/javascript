<!--
Meta Description: # ConstantSourceNode in JavaScript: Understanding AudioNode for Continuous Sound Generation ## Synopsis `ConstantSourceNode` is a specialized interfac...
Meta Keywords: constantsourcenode, audiocontext, audio, signal, constant
-->

# ConstantSourceNode in JavaScript: Understanding AudioNode for Continuous Sound Generation

## Synopsis
`ConstantSourceNode` is a specialized interface within the Web Audio API that allows developers to create a constant audio signal, which can be utilized for various audio processing tasks such as sound synthesis, testing, or creating continuous audio effects.

## Documentation
### Purpose
`ConstantSourceNode` is designed to generate a constant signal that can be used as an audio input. It is particularly useful for applications requiring a steady tone, like signal testing, or as a base for more complex audio processing.

### Usage
To use `ConstantSourceNode`, you must first create an instance of the `AudioContext` and then instantiate `ConstantSourceNode` through the context. The node can then be connected to other audio nodes in your audio graph.

### Constructor
```javascript
const constantSourceNode = new ConstantSourceNode(context, options);
```
- **context**: An instance of `AudioContext`.
- **options**: An optional object that can include:
  - `offset`: A number specifying the constant signal value, which defaults to 0.

### Methods
- **start(when)**: Begins playback of the constant signal.
- **stop(when)**: Stops playback of the constant signal.

### Properties
- **offset**: A `number` representing the constant signal value that is produced by the node.

### Example Usage
```javascript
// Create an AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Create a ConstantSourceNode
const constantSourceNode = new ConstantSourceNode(audioContext, { offset: 0.5 });

// Connect the node to the destination (speakers)
constantSourceNode.connect(audioContext.destination);

// Start the constant source
constantSourceNode.start();
```

## Examples
### Basic Example
In this example, a constant audio signal with an offset of 0.5 is generated and played through the speakers:

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const constantSourceNode = new ConstantSourceNode(audioContext, { offset: 0.5 });
constantSourceNode.connect(audioContext.destination);
constantSourceNode.start();
```

### Stopping the Signal
To stop the constant audio signal after a duration, you can use the `stop` method:

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const constantSourceNode = new ConstantSourceNode(audioContext, { offset: 0.5 });
constantSourceNode.connect(audioContext.destination);
constantSourceNode.start();

// Stop the signal after 5 seconds
setTimeout(() => {
  constantSourceNode.stop();
}, 5000);
```

## Explanation
### Common Pitfalls
1. **AudioContext State**: Ensure that the `AudioContext` is in a running state. If it is in a suspended state (e.g., due to user interaction requirements in web browsers), you must resume it before starting the `ConstantSourceNode`.
  
2. **Connecting Nodes**: Always connect the `ConstantSourceNode` to an output node, such as `audioContext.destination`, before calling `start()`; otherwise, you will not hear any audio.

3. **Multiple Starts and Stops**: A `ConstantSourceNode` can only be started and stopped once. Attempting to start it again after it has been stopped will throw an error. If you need to restart it, create a new instance.

4. **Offset Range**: While the `offset` property can take any numerical value, it’s important to remember that the output signal is typically interpreted as a range between 0 and 1 for audio applications.

## One Line Summary
`ConstantSourceNode` is a Web Audio API interface that generates a continuous audio signal, enabling developers to create steady tones for various audio applications.