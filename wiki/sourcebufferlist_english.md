<!--
Meta Description: # SourceBufferList in JavaScript: Comprehensive Guide ## Synopsis `SourceBufferList` is an interface that provides a collection of `SourceBuffer` obje...
Meta Keywords: sourcebuffer, mediasource, sourcebufferlist, media, video
-->

# SourceBufferList in JavaScript: Comprehensive Guide

## Synopsis
`SourceBufferList` is an interface that provides a collection of `SourceBuffer` objects, enabling developers to manage and manipulate media segments for playback in a more organized and efficient manner when working with the Media Source Extensions (MSE) API in JavaScript.

## Documentation

### Purpose
`SourceBufferList` is primarily used in conjunction with the `MediaSource` object to handle media streams dynamically. It allows developers to manage multiple `SourceBuffer` objects that hold media data, such as audio or video. This is particularly useful for applications that require streaming capabilities, such as video players or live broadcasts.

### Usage
The `SourceBufferList` object is automatically generated when you access the `sourceBuffers` property of a `MediaSource` instance. It allows developers to iterate over, add, or remove `SourceBuffer` objects. 

### Properties
- **length**: Returns the number of `SourceBuffer` objects in the list.
- **[index]**: Allows access to a specific `SourceBuffer` in the list by its index.

### Methods
- **item(index)**: Returns the `SourceBuffer` at the specified index.
- **forEach(callback)**: Executes a provided function once for each `SourceBuffer` in the list.

## Examples

### Basic Usage Example
```javascript
// Create a MediaSource instance
const mediaSource = new MediaSource();

// Add an event listener for 'sourceopen'
mediaSource.addEventListener('sourceopen', () => {
    const sourceBufferList = mediaSource.sourceBuffers;

    // Log the number of SourceBuffers
    console.log(`Number of SourceBuffers: ${sourceBufferList.length}`);

    // Create a new SourceBuffer
    const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8, vorbis"');

    // Add a new SourceBuffer to the list
    console.log(`New SourceBuffer added: ${sourceBufferList.length}`);
});

// Attach MediaSource to video element
const video = document.querySelector('video');
video.src = URL.createObjectURL(mediaSource);
```

### Iterating Through SourceBufferList
```javascript
const mediaSource = new MediaSource();
mediaSource.addEventListener('sourceopen', () => {
    const sourceBufferList = mediaSource.sourceBuffers;

    // Iterate and log each SourceBuffer
    sourceBufferList.forEach((buffer, index) => {
        console.log(`SourceBuffer ${index}:`, buffer);
    });
});
```

## Explanation

### Common Pitfalls
- **Accessing Before Source Open**: Attempting to access `sourceBuffers` before the `sourceopen` event is fired will result in an empty list. Always ensure that you wait for the `sourceopen` event.
- **Incorrect MIME Types**: When adding a new `SourceBuffer`, ensure the MIME type is supported by the browser. An unsupported MIME type will throw an error.
- **Buffering Issues**: If you try to append data to a `SourceBuffer` that is updating or in an error state, you may encounter exceptions. Always check the `updating` property before appending data.

### Additional Notes
`SourceBufferList` is fundamental for managing multiple streams in a single media context. It provides an efficient way to control playback and buffering, making it essential for developers building advanced media applications.

## One Line Summary
`SourceBufferList` is a collection of `SourceBuffer` objects used in the Media Source Extensions API to manage media segments for efficient streaming and playback in JavaScript.