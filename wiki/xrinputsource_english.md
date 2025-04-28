<!--
Meta Description: # Understanding XRInputSource in JavaScript: A Comprehensive Guide ## Synopsis XRInputSource is a key interface in the WebXR API that represents input...
Meta Keywords: input, session, inputsource, xrinputsource, access
-->

# Understanding XRInputSource in JavaScript: A Comprehensive Guide

## Synopsis
XRInputSource is a key interface in the WebXR API that represents input sources such as controllers and devices used in virtual and augmented reality experiences, enabling developers to access and manage input data from these devices in a standardized way.

## Documentation
### Purpose
The XRInputSource interface is designed to manage input from various XR devices. It provides developers with a consistent method to interact with user input in immersive environments, including motion controllers and other input methods.

### Usage
To utilize XRInputSource in a WebXR application, you typically access it through the `XRSession`'s `inputSources` property. Each input source can provide essential information such as the type of device, its capabilities, and the current state of input actions (like button presses or joystick movements).

### Properties
- **`handedness`**: A string that indicates whether the input source is from the left or right hand (e.g., "left", "right").
- **`targetRaySpace`**: A reference to the XRSpace that defines the position and orientation of the input source in the 3D space.
- **`gripSpace`**: An optional XRSpace that represents a more precise location for the input source, often used for tracking the grip of a controller.
- **`gamepad`**: An optional property that holds information about the associated gamepad, allowing access to buttons and axes.

### Methods
XRInputSource does not have methods of its own, but it allows access to the state of the input through its properties.

## Examples
### Example 1: Accessing Input Sources
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSource = event.inputSource;
        console.log('Input Source:', inputSource);
    });
    session.update();
});
```

### Example 2: Checking Handedness
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('inputsourceschange', (event) => {
        event.added.forEach((inputSource) => {
            console.log(`New Input Source Detected: ${inputSource.handedness}`);
        });
    });
});
```

### Example 3: Using the Gamepad Property
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSource = event.inputSource;
        if (inputSource.gamepad) {
            console.log('Button Pressed:', inputSource.gamepad.buttons[0].pressed);
        }
    });
});
```

## Explanation
### Common Pitfalls
- **Not Checking for Gamepad Availability**: Always ensure to check if the `gamepad` property exists before trying to access its buttons or axes to avoid runtime errors.
  
- **Async Behavior**: WebXR operations are asynchronous; make sure to handle promises correctly to prevent accessing input sources before they are ready.

- **Session State**: Ensure that the XR session is active when trying to access input sources, as attempts to access them during a non-active session will yield no results.

### Additional Notes
- The XRInputSource API is heavily dependent on the browser's WebXR implementation, which may vary across different devices and browsers.
- Testing should be performed on actual XR hardware to fully understand how input sources behave in a live environment.

## One Line Summary
XRInputSource is an interface in the WebXR API that allows developers to manage input from XR devices, enhancing user interaction in virtual and augmented reality experiences.