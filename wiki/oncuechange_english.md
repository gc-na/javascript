<!--
Meta Description: # oncuechange: Understanding the JavaScript Event for Media Element Cue Changes ## Synopsis The `oncuechange` event in JavaScript is triggered when th...
Meta Keywords: track, event, text, oncuechange, cue
-->

# oncuechange: Understanding the JavaScript Event for Media Element Cue Changes

## Synopsis
The `oncuechange` event in JavaScript is triggered when the active cue of a text track (like subtitles or captions) changes in a media element, such as `<video>` or `<audio>`. This event allows developers to respond to changes in the displayed text cues dynamically.

## Documentation

### Purpose
The `oncuechange` event is primarily used with HTML5 media elements that support text tracks. It provides a way to execute custom JavaScript code whenever the active cue in a text track changes, enabling better user interaction and enhancing accessibility features.

### Usage
To use the `oncuechange` event, you can assign it directly to a media element or use `addEventListener`. It is essential to ensure that the media element has a text track (e.g., subtitles or captions) defined.

```javascript
const videoElement = document.getElementById('myVideo');
videoElement.textTracks[0].mode = 'showing'; // Ensuring the track is visible

videoElement.ontimeupdate = function() {
    // Listening for cue changes
    const track = videoElement.textTracks[0];
    track.oncuechange = function() {
        const activeCue = track.activeCues[0]; // Get the active cue
        if (activeCue) {
            console.log(activeCue.text); // Log the text of the active cue
        }
    };
};
```

### Details
- **Event Type**: The `oncuechange` event is part of the TextTrack API.
- **Event Target**: This event is fired on the TextTrack object associated with a media element.
- **Supported Elements**: Works with `<video>` and `<audio>` elements that have text tracks defined.

## Examples

### Basic Usage Example
Here is a simple example demonstrating how to utilize the `oncuechange` event:

```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    <track kind="subtitles" src="subtitles_en.vtt" srclang="en" label="English">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');
    const track = video.textTracks[0]; // Access the first text track

    track.mode = 'showing'; // Ensure the track is visible

    track.oncuechange = function() {
        const activeCue = track.activeCues[0];
        if (activeCue) {
            console.log('Current Cue:', activeCue.text);
        }
    };
</script>
```

### Handling Multiple Cues
If there are multiple active cues, you can loop through them:

```javascript
track.oncuechange = function() {
    const activeCues = track.activeCues;
    for (let i = 0; i < activeCues.length; i++) {
        console.log('Active Cue:', activeCues[i].text);
    }
};
```

## Explanation
While using the `oncuechange` event, developers should keep the following in mind:
- **Performance**: Excessive logging or processing during the event can lead to performance issues, especially in videos playing at higher resolutions.
- **Browser Support**: Most modern browsers support the `oncuechange` event; however, always check for compatibility if targeting older browsers.
- **Track Mode**: Ensure that the text track mode is set to `'showing'` to receive cue change events.

## One Line Summary
The `oncuechange` event in JavaScript allows developers to detect and respond to changes in the active cues of text tracks in media elements, enhancing accessibility and user experience.