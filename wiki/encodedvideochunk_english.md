<!--
Meta Description: # EncodedVideoChunk in JavaScript: A Comprehensive Guide ## Synopsis `EncodedVideoChunk` is a JavaScript interface that represents a chunk of encoded ...
Meta Keywords: video, data, encodedvideochunk, chunk, encoded
-->

# EncodedVideoChunk in JavaScript: A Comprehensive Guide

## Synopsis
`EncodedVideoChunk` is a JavaScript interface that represents a chunk of encoded video data, facilitating the handling of video encoding and decoding in web applications, particularly in the context of the WebCodecs API.

## Documentation
### Purpose
The `EncodedVideoChunk` interface is part of the WebCodecs API, which allows developers to work with encoded media data directly in the browser. This API is designed to improve the performance of media applications by providing low-level access to video and audio streams. `EncodedVideoChunk` is specifically used to manage chunks of video data that have been encoded, allowing for efficient processing and playback.

### Usage
To use `EncodedVideoChunk`, you typically create an instance of the chunk with specific properties such as `type`, `timestamp`, and `data`. The chunks can then be sent to a video decoder or processed in other ways.

### Properties
- **type**: A string that indicates whether the chunk is a keyframe (`"key"`) or a non-keyframe (`"delta"`).
- **timestamp**: A number representing the presentation timestamp of the chunk, which helps synchronize video playback.
- **data**: An `ArrayBuffer` that contains the actual encoded video data.

### Constructor
The constructor for creating an `EncodedVideoChunk` looks like this:

```javascript
let videoChunk = new EncodedVideoChunk({
  type: 'key', // or 'delta'
  timestamp: 0, // in milliseconds
  data: encodedDataBuffer // ArrayBuffer containing the encoded data
});
```

## Examples
### Basic Usage Example
Here’s a simple example of creating an `EncodedVideoChunk`:

```javascript
// Assume 'encodedDataBuffer' is an ArrayBuffer containing encoded video data

const encodedDataBuffer = new ArrayBuffer(1024); // Example buffer
const videoChunk = new EncodedVideoChunk({
  type: 'key',
  timestamp: 0,
  data: encodedDataBuffer
});

console.log(videoChunk.type); // Output: "key"
console.log(videoChunk.timestamp); // Output: 0
```

### Sending to a Decoder
In a typical workflow, you might send this chunk to a video decoder like so:

```javascript
const decoder = new VideoDecoder({
  output: (chunk) => {
    console.log('Decoded chunk:', chunk);
  },
  error: (err) => {
    console.error('Decoder error:', err);
  }
});

// Queue the encoded video chunk for decoding
decoder.decode(videoChunk);
```

## Explanation
### Common Pitfalls
1. **Incorrect Buffer Size**: Ensure the `ArrayBuffer` provided is correctly sized and contains valid encoded video data. An improperly sized buffer may lead to errors during decoding.
2. **Type Mismatch**: Always specify the correct type (`"key"` or `"delta"`) based on the video's encoding. Using the wrong type can cause playback issues.
3. **Timestamp**: The `timestamp` should be in the correct units (milliseconds) and should correspond to the actual presentation timing of the video frame to prevent synchronization issues.

### Additional Notes
- The `EncodedVideoChunk` is closely tied with the `VideoDecoder` and `VideoEncoder`, making it essential to understand how these components interact within the WebCodecs API.
- The use of this API is still evolving, and developers should check for browser compatibility and updates to the specification.

## One Line Summary
`EncodedVideoChunk` is a JavaScript interface for representing chunks of encoded video data, enabling efficient media processing and playback in web applications.