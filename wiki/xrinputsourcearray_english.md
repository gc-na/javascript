<!--
Meta Description: # Understanding XRInputSourceArray in JavaScript: A Comprehensive Guide ## Synopsis XRInputSourceArray is a crucial component of the WebXR API, design...
Meta Keywords: input, xrinputsourcearray, source, session, sources
-->

# Understanding XRInputSourceArray in JavaScript: A Comprehensive Guide

## Synopsis
XRInputSourceArray is a crucial component of the WebXR API, designed to manage input sources from various XR (Extended Reality) devices in JavaScript applications. This allows developers to create more immersive experiences by effectively handling user interactions in virtual and augmented reality environments.

## Documentation
### Purpose
The XRInputSourceArray provides a structured way to access and manipulate input sources from XR devices, such as VR headsets and AR glasses. It serves as an interface for developers to interact with various input types, including controllers, hand tracking, and other input devices.

### Usage
The XRInputSourceArray is typically accessed through the `XRSession` interface, where it can be used to retrieve the current state of input sources during XR sessions. The array contains objects representing each input source, allowing developers to read properties such as the type of input device (e.g., controller or hand), its pose, and its associated features.

### Properties
- **length**: The number of input sources currently available.
- **[index]**: Accesses the input source at a specific index.

### Methods
The XRInputSourceArray itself does not provide methods but is used in conjunction with various WebXR APIs, such as:
- `getInputSources()`: Retrieves the current input sources during an XR session.

## Examples
### Basic Usage Example

```javascript
let xrSession = null;

// Start an XR session
navigator.xr.requestSession('immersive-vr').then((session) => {
    xrSession = session;

    // Add an event listener for the 'select' event
    session.addEventListener('select', (event) => {
        const inputSources = session.inputSources; // Access XRInputSourceArray

        inputSources.forEach((inputSource) => {
            console.log(`Input Source Type: ${inputSource.targetRayMode}`);
            console.log(`Input Source Handedness: ${inputSource.handedness}`);
        });
    });
});
```

### Accessing Input Source Properties Example

```javascript
function handleXRFrame(frame) {
    const inputSources = frame.session.inputSources; // Access XRInputSourceArray

    inputSources.forEach((source) => {
        if (source.gripSpace) {
            console.log(`Grip Space: ${source.gripSpace}`);
        }
        if (source.targetRaySpace) {
            console.log(`Target Ray Space: ${source.targetRaySpace}`);
        }
    });
}
```

## Explanation
### Common Pitfalls
- **Session Not Started**: Ensure that the XR session is active before trying to access the `inputSources`. Attempting to access the array when the session is not started will result in an error.
- **Outdated Browser Support**: Make sure to check for browser compatibility with the WebXR API, as some features may not be supported in all browsers.
- **Index Out of Bounds**: When accessing input sources by index, always check the length of the XRInputSourceArray to avoid out-of-bounds errors.

### Additional Notes
- Input sources may change over time, especially in dynamic environments where devices are added or removed. Always handle these changes gracefully.
- The XRInputSourceArray can contain different types of input sources, so it’s essential to check the `targetRayMode` and other properties to determine the appropriate handling logic.

## One Line Summary
XRInputSourceArray is a vital interface in the WebXR API for managing input sources from XR devices in JavaScript applications, allowing for rich user interactions in immersive environments.