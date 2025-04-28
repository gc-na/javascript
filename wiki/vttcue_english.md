<!--
Meta Description: # VTTCue in JavaScript: A Comprehensive Guide to WebVTT Cue Management ## Synopsis VTTCue is a JavaScript interface that represents a cue in the WebVT...
Meta Keywords: cue, video, vttcue, text, track
-->

# VTTCue in JavaScript: A Comprehensive Guide to WebVTT Cue Management

## Synopsis
VTTCue is a JavaScript interface that represents a cue in the WebVTT (Web Video Text Tracks) format, enabling developers to create, manage, and manipulate subtitles and captions in HTML5 video elements.

## Documentation

### Purpose
The VTTCue object is used primarily for providing text tracks (such as subtitles, captions, or descriptions) in HTML5 video players. It allows developers to define the content, timing, and positioning of text that appears over video playback, enhancing accessibility and user experience.

### Usage
To utilize VTTCue, it is generally employed alongside the HTML `<track>` element within a `<video>` element. The cues can be programmatically created and manipulated using the VTTCue constructor.

#### Syntax
```javascript
let cue = new VTTCue(startTime, endTime, text);
```
- **startTime**: The time in seconds when the cue should appear.
- **endTime**: The time in seconds when the cue should disappear.
- **text**: The string of text that will be displayed during the cue's active period.

### Properties
- `startTime`: The cue's start time in seconds.
- `endTime`: The cue's end time in seconds.
- `text`: The text of the cue.

### Methods
- **`getCueAsHTML()`**: Returns the text of the cue as an HTML string, which can be useful for styling.

## Examples

### Basic Usage
Here’s a simple example of how to create and use a VTTCue in a video with HTML5:

```html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <track kind="subtitles" src="subtitles.vtt" srclang="en" label="English">
</video>

<script>
  const videoElement = document.querySelector('video');
  const trackElement = videoElement.querySelector('track');

  trackElement.track.mode = 'hidden'; // Set the track mode to hidden

  const cue = new VTTCue(0, 5, 'Welcome to the video!'); // Create a new cue
  trackElement.track.addCue(cue); // Add the cue to the track

  // Example of how to access and manipulate the cue
  console.log(cue.getCueAsHTML()); // Outputs: Welcome to the video!
</script>
```

### Adding Multiple Cues
You can also add multiple cues to a track:

```javascript
const cue1 = new VTTCue(0, 5, 'Welcome!');
const cue2 = new VTTCue(5, 10, 'Enjoy the show!');
trackElement.track.addCue(cue1);
trackElement.track.addCue(cue2);
```

## Explanation

### Common Pitfalls
1. **Timing Issues**: Ensure that the start and end times of the cues do not overlap and are properly sequenced.
2. **Track Mode**: The default mode of a track is "disabled". Make sure to set it to "hidden" or "showing" to see the cues during playback.
3. **Browser Support**: While VTTCue is widely supported in modern browsers, always check for compatibility if targeting older versions.

### Additional Notes
- VTTCue is part of the WebVTT specification, which is designed for displaying timed text tracks in HTML5 media.
- Using styling in conjunction with VTTCue can enhance the visual presentation of the text cues.
- Always test cues in the context of the video to ensure proper timing and display.

## One Line Summary
VTTCue is a JavaScript object for managing timed text cues in HTML5 video elements, enhancing accessibility and user engagement through subtitles and captions.