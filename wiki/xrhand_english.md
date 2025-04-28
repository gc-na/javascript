<!--
Meta Description: # XRHand: JavaScript Interface for Hand Tracking in WebXR ## Synopsis XRHand is a JavaScript interface used in WebXR to represent and manage hand trac...
Meta Keywords: hand, xrhand, tracking, data, joint
-->

# XRHand: JavaScript Interface for Hand Tracking in WebXR

## Synopsis
XRHand is a JavaScript interface used in WebXR to represent and manage hand tracking data for immersive web experiences. It provides developers with the ability to access real-time hand pose information within virtual and augmented reality environments.

## Documentation

### Purpose
XRHand is part of the WebXR Device API, which allows developers to create applications that can access and utilize virtual and augmented reality hardware. The XRHand interface specifically focuses on hand tracking capabilities, enabling applications to interpret hand positions, gestures, and movements.

### Usage
The XRHand interface is typically used in conjunction with the XRSession and XRFrame interfaces. It allows developers to obtain hand tracking data during a WebXR session, which can be used for various interactive applications, such as games, simulations, or virtual meetings.

To access an instance of XRHand, developers can retrieve hand data from the XRFrame object during the rendering loop of a WebXR session. The hands are represented as XRHand objects, which provide properties and methods to access joint positions and other relevant hand data.

### Key Properties
- **joints**: An array of XRJoint objects representing the positions and orientations of individual joints in the hand.
- **inputSource**: Represents the input source (left or right hand) associated with this XRHand.

### Initialization Example
To use XRHand, first ensure that your application has initiated a WebXR session:

```javascript
const xrSession = await navigator.xr.requestSession('immersive-vr');
xrSession.addEventListener('end', onSessionEnded);

const referenceSpace = await xrSession.requestReferenceSpace('local');
const xrFrame = await xrSession.requestAnimationFrame(onXRFrame);

function onXRFrame(time, frame) {
  const session = frame.session;
  const handData = frame.getPose(xrHand, referenceSpace); // Accessing hand data
  // Process hand data...
}
```

## Examples

### Basic Hand Tracking Example
Here is a simple example demonstrating how to access hand tracking data:

```javascript
xrSession.addEventListener('selectstart', (event) => {
  const hand = event.inputSource.hand; // Access the XRHand instance
  const joints = hand.joints; // Get the joints array

  // Log joint positions
  joints.forEach((joint) => {
    console.log(`Joint: ${joint.name}, Position: ${joint.position}`);
  });
});
```

### Gesture Recognition Example
Implementing gesture recognition using hand tracking data:

```javascript
function checkGesture(hand) {
  if (hand.joints) {
    const thumbTip = hand.joints.find(joint => joint.name === 'thumbTip');
    const indexTip = hand.joints.find(joint => joint.name === 'indexTip');

    if (thumbTip && indexTip) {
      const distance = calculateDistance(thumbTip.position, indexTip.position);
      if (distance < 0.05) { // Example threshold for a pinch gesture
        console.log('Pinch gesture detected!');
      }
    }
  }
}
```

## Explanation
### Common Pitfalls
- **Browser Compatibility**: Ensure that the browser supports WebXR and hand tracking features. Not all browsers may have complete support for XRHand.
- **Session Management**: Incorrect handling of XRSession lifecycle events (start, end) can lead to unexpected behavior. Always manage session states properly.
- **Performance Considerations**: Hand tracking can be resource-intensive. Optimize rendering loops and consider throttling updates to improve performance.

### Additional Notes
- The accuracy of hand tracking can vary based on the hardware being used. Always test on target devices.
- Be mindful of user privacy and ensure that hand tracking data is handled securely.

## One Line Summary
XRHand is a JavaScript interface for accessing real-time hand tracking data in immersive WebXR applications.