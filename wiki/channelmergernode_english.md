<!--
Meta Description: # ChannelMergerNode in JavaScript: Merging Multiple Audio Streams ## Synopsis The `ChannelMergerNode` is a part of the Web Audio API in JavaScript tha...
Meta Keywords: audio, audiocontext, connect, channelmergernode, merger
-->

# ChannelMergerNode in JavaScript: Merging Multiple Audio Streams

## Synopsis
The `ChannelMergerNode` is a part of the Web Audio API in JavaScript that allows developers to combine multiple audio channels into a single audio stream, enabling complex audio manipulation and playback in web applications.

## Documentation
### Purpose
`ChannelMergerNode` is designed to merge multiple audio input streams into one output stream. This is particularly useful in audio applications that require the mixing of different sound sources, such as music, sound effects, or voice inputs.

### Usage
To create a `ChannelMergerNode`, you need to obtain an `AudioContext` and call its `createChannelMerger` method. The `ChannelMergerNode` can handle up to six input channels, allowing for flexible mixing options.

### Syntax
```javascript
const audioContext = new AudioContext();
const channelMerger = audioContext.createChannelMerger(numberOfOutputs);
```
- `numberOfOutputs`: (Optional) Specifies the number of output channels. Defaults to `1`.

### Properties
- **Channel Count**: The `ChannelMergerNode` can be configured to merge up to 6 input channels.
- **Channel Count Mode**: Determines how the audio channels are handled, with options like "max" and "explicit."

### Methods
- **connect(destination)**: Connects the `ChannelMergerNode` to another audio node or audio context destination.

## Examples
### Example 1: Merging Two Audio Tracks
```javascript
const audioContext = new AudioContext();
const merger = audioContext.createChannelMerger(2);

const audioSource1 = audioContext.createBufferSource();
const audioSource2 = audioContext.createBufferSource();

// Load audio data into audioSource1 and audioSource2 here
// ...

// Connect sources to the merger
audioSource1.connect(merger, 0, 0); // Connect first audio track to the first channel
audioSource2.connect(merger, 0, 1); // Connect second audio track to the second channel

// Connect the merger to the destination (speakers)
merger.connect(audioContext.destination);

// Start playback
audioSource1.start();
audioSource2.start();
```

### Example 2: Merging Multiple Channels
```javascript
const audioContext = new AudioContext();
const merger = audioContext.createChannelMerger(6);

// Connect multiple sources
for (let i = 0; i < 6; i++) {
    const audioSource = audioContext.createBufferSource();
    // Load audio data into audioSource here
    // ...
    audioSource.connect(merger, 0, i); // Connect each source to a different channel
}

// Connect the merger to the destination
merger.connect(audioContext.destination);

// Start playback of all sources
for (let i = 0; i < 6; i++) {
    audioSource.start();
}
```

## Explanation
### Common Pitfalls
- **Not Connecting to Destination**: Failing to connect the `ChannelMergerNode` to the audio context's destination will result in no sound output.
- **Buffer Sources**: Ensure that audio buffers are properly loaded before attempting to start playback.
- **Browser Compatibility**: Not all browsers may support the full range of features in the Web Audio API, so testing across different environments is recommended.

### Gotchas
- **Channel Limitations**: Keep in mind the maximum of six channels that `ChannelMergerNode` can handle.
- **Volume Control**: The `ChannelMergerNode` does not manage volume levels. To adjust volume, consider using `GainNode`.

## One Line Summary
The `ChannelMergerNode` in JavaScript allows developers to efficiently combine multiple audio streams into a single output for enhanced audio playback and manipulation.