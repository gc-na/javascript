<!--
Meta Description: # Understanding XRInputSourcesChangeEvent in JavaScript: A Comprehensive Guide ## Synopsis The `XRInputSourcesChangeEvent` is an event in the WebXR AP...
Meta Keywords: event, input, sources, inputsources, source
-->

# Understanding XRInputSourcesChangeEvent in JavaScript: A Comprehensive Guide

## Synopsis
The `XRInputSourcesChangeEvent` is an event in the WebXR API that notifies developers when the input sources (such as controllers or hand tracking) change in a virtual reality (VR) or augmented reality (AR) environment. This event is crucial for managing user interactions in immersive experiences.

## Documentation

### Purpose
The `XRInputSourcesChangeEvent` is designed to provide notifications for changes in the input sources that an XR session can use. These changes can include the addition or removal of input devices, allowing developers to adjust their application’s behavior accordingly.

### Usage
To utilize the `XRInputSourcesChangeEvent`, developers must listen for this event on the XR session. The event is triggered whenever the input sources change, providing an updated list of the current input sources.

### Event Properties
- **type**: A string representing the type of event (always "inputsourceschange").
- **session**: The XRSession object that this event is associated with.
- **inputSources**: An array of `XRInputSource` objects representing the current input sources available in the session.

### Listening for the Event
To listen for `XRInputSourcesChangeEvent`, you can use the following code snippet:

```javascript
// Assuming 'xrSession' is an active XRSession
xrSession.addEventListener('inputsourceschange', (event) => {
    console.log('Input sources changed:', event.inputSources);
});
```

## Examples

### Basic Example
Here’s a simple example of how to handle input source changes in a VR session:

```javascript
const xrSession = await navigator.xr.requestSession('immersive-vr');

xrSession.addEventListener('inputsourceschange', (event) => {
    event.inputSources.forEach((inputSource) => {
        console.log('Input Source:', inputSource);
    });
});

// Start the XR session
await xrSession.start();
```

### Handling Input Source Addition and Removal
You might want to keep track of existing input sources and respond to additions or removals:

```javascript
const inputSources = new Map();

xrSession.addEventListener('inputsourceschange', (event) => {
    event.inputSources.forEach((inputSource) => {
        if (!inputSources.has(inputSource.hand)) {
            console.log('Input source added:', inputSource);
            inputSources.set(inputSource.hand, inputSource);
        }
    });

    inputSources.forEach((source, hand) => {
        if (!event.inputSources.includes(source)) {
            console.log('Input source removed:', source);
            inputSources.delete(hand);
        }
    });
});
```

## Explanation

### Common Pitfalls
- **Event Not Triggering**: Ensure that your XR session is active and that you have properly set up event listeners. If the session is not started, the event will not be triggered.
- **Input Source Properties**: Be aware that the properties of `XRInputSource` may vary based on the device being used. Always check for the availability of properties before using them.

### Gotchas
- **Multiple Input Sources**: Applications may receive multiple input source changes in a single event. It’s essential to handle the array of input sources in your listener appropriately.
- **Device Compatibility**: Not all devices support all types of input sources. Always test your application across different hardware to ensure consistent behavior.

## One Line Summary
The `XRInputSourcesChangeEvent` in JavaScript notifies developers of changes to input sources in an XR session, allowing for dynamic user interaction management.