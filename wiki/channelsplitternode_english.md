<!--
Meta Description: # ChannelSplitterNode in JavaScript: An In-Depth Guide ## Synopsis The `ChannelSplitterNode` is a part of the Web Audio API that allows developers to ...
Meta Keywords: audiocontext, connect, audio, const, splitter
-->

# ChannelSplitterNode in JavaScript: An In-Depth Guide

## Synopsis
The `ChannelSplitterNode` is a part of the Web Audio API that allows developers to separate audio streams into multiple channels, enabling advanced audio processing and manipulation in JavaScript applications.

## Documentation

### Purpose
The `ChannelSplitterNode` is designed to split an audio signal into its constituent channels. For instance, a stereo signal can be split into two separate mono signals, allowing for independent processing of each channel. This functionality is essential in audio applications where individual channel manipulation is necessary, such as in mixing, effects processing, or spatialization.

### Usage
To create a `ChannelSplitterNode`, you need to instantiate it using the `AudioContext` interface. The number of output channels can be specified during creation, with a default of 6 channels.

#### Syntax
```javascript
const channelSplitterNode = audioContext.createChannelSplitter(numberOfOutputs);
```

- **audioContext**: An instance of `AudioContext`.
- **numberOfOutputs**: (optional) An integer representing the number of channels to split, ranging from 1 to 32.

### Constructor Example
```javascript
const audioContext = new AudioContext();
const splitter = audioContext.createChannelSplitter(2); // Creates a splitter for 2 channels
```

## Examples

### Basic Example
Here’s a simple example demonstrating how to use the `ChannelSplitterNode` to split a stereo audio signal into left and right channels.

```javascript
// Create an AudioContext
const audioContext = new AudioContext();

// Create a source (e.g., from an audio file)
const audioElement = new Audio('audio-file.mp3');
const sourceNode = audioContext.createMediaElementSource(audioElement);

// Create a ChannelSplitterNode
const splitter = audioContext.createChannelSplitter(2);

// Connect the source to the splitter
sourceNode.connect(splitter);

// Connect the left channel to a gain node
const leftGain = audioContext.createGain();
splitter.connect(leftGain, 0); // Left channel

// Connect the right channel to a different gain node
const rightGain = audioContext.createGain();
splitter.connect(rightGain, 1); // Right channel

// Connect gain nodes to the destination
leftGain.connect(audioContext.destination);
rightGain.connect(audioContext.destination);

// Start playback
audioElement.play();
```

### Advanced Example
In this example, we apply different gain values to the left and right channels to demonstrate independent processing.

```javascript
// Create an AudioContext
const audioContext = new AudioContext();
const audioElement = new Audio('audio-file.mp3');
const sourceNode = audioContext.createMediaElementSource(audioElement);
const splitter = audioContext.createChannelSplitter(2);

// Connect source to splitter
sourceNode.connect(splitter);

// Create gain nodes for each channel
const leftGain = audioContext.createGain();
const rightGain = audioContext.createGain();

// Set gain values
leftGain.gain.value = 0.5; // Reduce left channel volume
rightGain.gain.value = 1.5; // Increase right channel volume

// Connect splitter outputs to gain nodes
splitter.connect(leftGain, 0); // Left channel
splitter.connect(rightGain, 1); // Right channel

// Connect gain nodes to destination
leftGain.connect(audioContext.destination);
rightGain.connect(audioContext.destination);

// Start playback
audioElement.play();
```

## Explanation
When working with `ChannelSplitterNode`, it's crucial to be aware of the following:

1. **Channel Count**: The maximum number of channels you can split into is dependent on the audio hardware and the environment. Always check the capabilities of the audio context you are working with.
  
2. **Order of Connections**: Ensure that you connect the source node to the splitter before connecting the splitter outputs to other nodes. Incorrect connection order may lead to audio issues.

3. **Audio Context State**: Be mindful of the `AudioContext` state when starting playback. If the context is in a suspended state, you might need to call `audioContext.resume()`.

4. **Handling Multiple Channels**: If splitting into more channels than available, the outputs will contain silence for the unused channels.

## One Line Summary
The `ChannelSplitterNode` in JavaScript allows developers to split an audio signal into multiple channels for independent processing in the Web Audio API.