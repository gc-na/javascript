<!--
Meta Description: # IIRFilterNode: Implementing Infinite Impulse Response Filters in JavaScript ## Synopsis The `IIRFilterNode` is a specialized interface in the Web Au...
Meta Keywords: iirfilternode, audiocontext, audio, coefficients, const
-->

# IIRFilterNode: Implementing Infinite Impulse Response Filters in JavaScript

## Synopsis
The `IIRFilterNode` is a specialized interface in the Web Audio API that allows developers to create and manipulate digital filters using Infinite Impulse Response (IIR) algorithms, enabling precise audio processing in web applications.

## Documentation

### Purpose
`IIRFilterNode` provides a way to apply complex filtering effects to audio signals in real time. This node allows developers to define the characteristics of the filter using coefficients, enabling sound manipulation for various applications such as audio mixing, sound design, and effects processing.

### Usage
To use `IIRFilterNode`, you must first create an `AudioContext` and then instantiate the `IIRFilterNode` with the appropriate coefficients for your filter. The coefficients determine the filter's behavior, including its frequency response and damping characteristics.

### Syntax
```javascript
const audioContext = new AudioContext();
const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);
```

### Parameters
- **feedforward**: An array of coefficients for the feedforward part of the filter.
- **feedback**: An array of coefficients for the feedback part of the filter.

### Properties
- **frequency**: Represents the frequency response of the filter.
- **gain**: Adjusts the amplitude of the filtered signal.

### Methods
- **connect(destination)**: Connects the `IIRFilterNode` to another audio node for further processing.
- **disconnect(destination)**: Disconnects the node from the specified audio node.

## Examples

### Basic Example: Applying an IIR Filter
```javascript
const audioContext = new AudioContext();
const feedforward = [0.3, 0.3]; // Example feedforward coefficients
const feedback = [0.2, -0.1]; // Example feedback coefficients

const iirFilterNode = audioContext.createIIRFilter(feedforward, feedback);
const oscillator = audioContext.createOscillator();

oscillator.connect(iirFilterNode);
iirFilterNode.connect(audioContext.destination);

oscillator.start();
```

### Example: Filtering Audio Input
```javascript
navigator.mediaDevices.getUserMedia({ audio: true })
  .then(stream => {
    const source = audioContext.createMediaStreamSource(stream);
    const iirFilterNode = audioContext.createIIRFilter([0.5], [0.5]);
    
    source.connect(iirFilterNode);
    iirFilterNode.connect(audioContext.destination);
  })
  .catch(error => {
    console.error('Error accessing audio input:', error);
  });
```

## Explanation
When using `IIRFilterNode`, the order and values of the coefficients are crucial. Incorrect values can lead to instability or unintended audio artifacts. It is also important to note that `IIRFilterNode` is not supported in Internet Explorer and may have varying levels of support in other browsers. Always check for compatibility and consider fallbacks for unsupported browsers.

### Common Pitfalls
- **Coefficient Values**: Ensure that the coefficients are within the valid range to avoid distortion or unwanted filtering effects.
- **Browser Support**: Verify the compatibility of `IIRFilterNode` with the target browsers to ensure users have a consistent experience.
- **AudioContext State**: Always check if the `AudioContext` is in a running state before creating or connecting nodes.

## One Line Summary
`IIRFilterNode` in JavaScript provides a powerful way to implement real-time audio filtering using Infinite Impulse Response algorithms within the Web Audio API.