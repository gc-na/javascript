<!--
Meta Description: # AudioBufferSourceNode in JavaScript: A Comprehensive Guide ## Synopsis The `AudioBufferSourceNode` is an essential interface in the Web Audio API th...
Meta Keywords: audio, audiocontext, audiobuffersourcenode, audiobuffer, data
-->

# AudioBufferSourceNode in JavaScript: A Comprehensive Guide

## Synopsis
The `AudioBufferSourceNode` is an essential interface in the Web Audio API that enables developers to play audio data stored in an `AudioBuffer`. It is commonly used for playing back recorded sound or sound effects in web applications.

## Documentation
### Purpose
The `AudioBufferSourceNode` is designed to facilitate audio playback from an `AudioBuffer`, which contains audio data. It can be used for a variety of applications, including music playback, sound effects, and interactive audio experiences.

### Usage
To create an `AudioBufferSourceNode`, you must first have an `AudioContext` and an `AudioBuffer` loaded with audio data. The basic workflow involves:

1. Creating an `AudioContext`.
2. Loading audio data into an `AudioBuffer`.
3. Creating an `AudioBufferSourceNode` from the `AudioContext`.
4. Connecting the node to the audio context's destination.
5. Starting playback using the `start()` method.

### Properties
- **buffer**: The `AudioBuffer` containing the audio data.
- **loop**: A boolean value indicating whether to loop the audio playback.
- **loopStart**: The starting point of the loop in seconds.
- **loopEnd**: The ending point of the loop in seconds.

### Methods
- **start()**: Begins playback of the audio, with optional parameters for start time and duration.
- **stop()**: Stops playback of the audio.

### Example Code
Here is a basic example of how to use `AudioBufferSourceNode`:

```javascript
// Step 1: Create an AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// Step 2: Load an audio file into an AudioBuffer
fetch('path/to/audiofile.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(audioBuffer => {
    // Step 3: Create an AudioBufferSourceNode
    const source = audioContext.createBufferSource();
    source.buffer = audioBuffer; // Assign the loaded AudioBuffer to the source

    // Step 4: Connect the source to the destination
    source.connect(audioContext.destination);
    
    // Step 5: Start playback
    source.start(0);
  })
  .catch(error => console.error('Error with fetching audio file:', error));
```

## Explanation
### Common Pitfalls
1. **AudioContext State**: Make sure the `AudioContext` is in a "running" state before trying to play audio. If the context is suspended, you may need to resume it with `audioContext.resume()`.
   
2. **Cross-Origin Issues**: If you're loading audio from a different origin, you may encounter CORS issues. Ensure that the server hosting the audio file allows cross-origin requests.

3. **Single Use**: An `AudioBufferSourceNode` can only be played once. If you need to replay the sound, you'll need to create a new instance of `AudioBufferSourceNode`.

4. **Asynchronous Loading**: Be aware that loading and decoding audio data is asynchronous. Ensure that you handle the promises properly to avoid trying to play audio before it's loaded.

### Additional Notes
- The `AudioBufferSourceNode` is useful for playing short audio samples and sound effects, while longer audio tracks may be better handled using other methods.
- You can adjust playback properties like volume and speed by using additional nodes in the audio context, such as `GainNode` for volume control.

## One Line Summary
The `AudioBufferSourceNode` in JavaScript is an interface that allows for the playback of audio data stored in an `AudioBuffer`, making it crucial for audio applications on the web.