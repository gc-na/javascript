<!--
Meta Description: # MediaStreamTrackVideoStats in JavaScript: Understanding Video Track Statistics ## Synopsis `MediaStreamTrackVideoStats` is a JavaScript interface th...
Meta Keywords: video, report, mediastreamtrackvideostats, statistics, console
-->

# MediaStreamTrackVideoStats in JavaScript: Understanding Video Track Statistics

## Synopsis
`MediaStreamTrackVideoStats` is a JavaScript interface that provides detailed statistics about the video tracks of a MediaStream, aiding developers in monitoring video performance and quality in real-time applications such as video conferencing and streaming.

## Documentation
### Purpose
The `MediaStreamTrackVideoStats` interface is part of the WebRTC API, specifically designed to gather and report statistics related to video tracks within a `MediaStream`. This data is crucial for developers who need to analyze video quality, detect issues, and optimize the user experience in applications that utilize real-time video communication.

### Usage
The `MediaStreamTrackVideoStats` can be accessed via the `getStats()` method provided by the `RTCPeerConnection` interface. When called, this method returns a `RTCStatsReport`, which includes instances of `MediaStreamTrackVideoStats` for each video track.

### Properties
- **frameWidth**: The width of the video frame in pixels.
- **frameHeight**: The height of the video frame in pixels.
- **framesPerSecond**: The number of frames being captured per second.
- **framesSent**: The total number of frames sent.
- **framesDropped**: The number of frames that were dropped during transmission.
- **bitrate**: The average bitrate of the video stream.

### Example Usage
Here's a basic example of how to access video track statistics using `MediaStreamTrackVideoStats`:

```javascript
const peerConnection = new RTCPeerConnection();

// Assuming video tracks have been added to the peer connection
peerConnection.getStats(null).then(stats => {
    stats.forEach(report => {
        if (report.type === 'video') {
            console.log(`Width: ${report.frameWidth}`);
            console.log(`Height: ${report.frameHeight}`);
            console.log(`Frames per second: ${report.framesPerSecond}`);
            console.log(`Frames sent: ${report.framesSent}`);
            console.log(`Frames dropped: ${report.framesDropped}`);
            console.log(`Bitrate: ${report.bitrate}`);
        }
    });
}).catch(error => {
    console.error('Error getting stats:', error);
});
```

## Explanation
### Common Pitfalls
1. **Asynchronous Calls**: The `getStats()` method is asynchronous. Failing to handle promises correctly can lead to unhandled rejections or missing stats data.
2. **Data Availability**: Statistics are only available if the video track is active. If the track is not being transmitted, you may receive incomplete data.
3. **Browser Compatibility**: Ensure that the browsers being targeted support the WebRTC API and `MediaStreamTrackVideoStats`, as implementations may vary.

### Additional Notes
- Video stats can change dynamically, so it's best to periodically call `getStats()` to keep your application updated on the current video quality.
- The statistics can be useful for debugging performance issues, such as high latency or low frame rates, which can significantly affect user experience.

## One Line Summary
`MediaStreamTrackVideoStats` provides essential statistics for monitoring and optimizing video tracks in JavaScript-based real-time applications.