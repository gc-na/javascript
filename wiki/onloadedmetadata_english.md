<!--
Meta Description: # Understanding the "onloadedmetadata" Event in JavaScript ## Synopsis The `onloadedmetadata` event in JavaScript is a critical event that triggers wh...
Meta Keywords: video, event, onloadedmetadata, media, duration
-->

# Understanding the "onloadedmetadata" Event in JavaScript

## Synopsis
The `onloadedmetadata` event in JavaScript is a critical event that triggers when metadata for a media element (like `<audio>` or `<video>`) has been loaded, allowing developers to access properties such as duration, dimensions, and more.

## Documentation

### Purpose
The `onloadedmetadata` event is used to handle the moment when the metadata of a media resource is fully loaded. This event is essential for media playback applications, as it allows developers to gather necessary information about the media file before playback starts.

### Usage
To utilize the `onloadedmetadata` event, you can assign an event listener to a media element (e.g., `<audio>` or `<video>`). This can be done using either HTML attributes or JavaScript methods. 

#### HTML Example:
```html
<video id="myVideo" onloadedmetadata="metadataLoaded()">
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support video.
</video>
```

#### JavaScript Example:
```javascript
const videoElement = document.getElementById('myVideo');
videoElement.onloadedmetadata = function() {
    console.log('Metadata loaded!');
};
```

### Details
The `onloadedmetadata` event is significant for accessing media properties, such as:
- `duration`: Length of the media in seconds.
- `videoWidth` and `videoHeight`: Dimensions of the video.
- `tracks`: Information about the available text tracks.

This event can be critical for user experience, as it allows developers to implement features like displaying the media duration before playback starts or dynamically adjusting the UI based on the media dimensions.

## Examples

### Example 1: Accessing Video Duration
```html
<video id="videoElement" controls>
    <source src="example.mp4" type="video/mp4">
    Your browser does not support video.
</video>

<script>
document.getElementById('videoElement').onloadedmetadata = function() {
    const duration = this.duration; // Get video duration
    console.log(`Video Duration: ${duration} seconds`);
};
</script>
```

### Example 2: Displaying Video Dimensions
```html
<video id="videoElement" controls>
    <source src="example.mp4" type="video/mp4">
    Your browser does not support video.
</video>

<div id="videoInfo"></div>

<script>
document.getElementById('videoElement').onloadedmetadata = function() {
    const width = this.videoWidth; // Get video width
    const height = this.videoHeight; // Get video height
    document.getElementById('videoInfo').innerText = `Dimensions: ${width}x${height}`;
};
</script>
```

## Explanation
While the `onloadedmetadata` event is straightforward to implement, there are a few common pitfalls to be aware of:
- **Event Timing**: If you try to access media properties before the `onloadedmetadata` event fires, you may encounter `undefined` values. Always ensure that your code that accesses properties is inside the event handler.
- **Multiple Sources**: If there are multiple sources specified for a media element, the event will fire when the metadata for the first successfully loaded source is available. If the first source fails to load, the event may not fire.
- **Browser Compatibility**: While modern browsers generally support the `onloadedmetadata` event, always check for compatibility if your application needs to support older versions.

## One Line Summary
The `onloadedmetadata` event in JavaScript is triggered when metadata for a media element is loaded, allowing access to essential media properties like duration and dimensions.