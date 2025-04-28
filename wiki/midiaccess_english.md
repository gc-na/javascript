<!--
Meta Description: # Understanding MIDIAccess in JavaScript: A Comprehensive Guide ## Synopsis MIDIAccess is a JavaScript interface that provides access to MIDI (Musical...
Meta Keywords: midi, midiaccess, access, devices, input
-->

# Understanding MIDIAccess in JavaScript: A Comprehensive Guide

## Synopsis
MIDIAccess is a JavaScript interface that provides access to MIDI (Musical Instrument Digital Interface) devices, enabling web applications to communicate with MIDI hardware for interactive music creation and manipulation.

## Documentation

### Purpose
The MIDIAccess interface allows developers to interact with MIDI devices (such as keyboards, drum machines, and synthesizers) connected to a user's computer. This interface is part of the Web MIDI API, which aims to enhance web applications by allowing real-time audio and music interaction.

### Usage
To use MIDIAccess, you must first request access to MIDI devices. The `navigator.requestMIDIAccess()` method is utilized to initiate this process. Once access is granted, you can enumerate available MIDI inputs and outputs and set up event listeners to handle MIDI messages.

### Details
1. **Requesting Access**: The `navigator.requestMIDIAccess()` method returns a promise that resolves to a MIDIAccess object if access is granted.
2. **MIDIAccess Object**: This object contains properties for retrieving input and output ports, as well as methods for listening to MIDI messages.
3. **MIDI Messages**: MIDI messages are transmitted as arrays of numbers, with each message type corresponding to specific actions (e.g., note on, note off, control change).

### Syntax
```javascript
navigator.requestMIDIAccess()
  .then(successCallback, errorCallback);
```

### Properties
- **inputs**: A read-only property that returns a `Map` of all available MIDI input ports.
- **outputs**: A read-only property that returns a `Map` of all available MIDI output ports.

### Methods
- **onstatechange**: An event handler property that is triggered when a MIDI device is connected or disconnected.

## Examples

### Example 1: Requesting MIDI Access
```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    console.log('MIDI Access Granted:', midiAccess);
}

function onMIDIFailure() {
    console.error('Could not access your MIDI devices.');
}
```

### Example 2: Listing MIDI Inputs
```javascript
navigator.requestMIDIAccess().then(midiAccess => {
    const inputs = midiAccess.inputs;
    for (let input of inputs.values()) {
        console.log('MIDI Input:', input.name);
    }
});
```

### Example 3: Receiving MIDI Messages
```javascript
navigator.requestMIDIAccess().then(midiAccess => {
    const input = midiAccess.inputs.values().next().value; // Get the first available input
    input.onmidimessage = (message) => {
        const [status, note, velocity] = message.data;
        console.log(`MIDI Message: Status: ${status}, Note: ${note}, Velocity: ${velocity}`);
    };
});
```

## Explanation
### Common Pitfalls
- **Permissions**: Users may need to grant permission to access MIDI devices. If permission is denied, the promise will be rejected.
- **Browser Support**: Ensure that the browser supports the Web MIDI API. Not all browsers have full support, so check compatibility.
- **MIDI Device Connection**: Devices must be connected and recognized by the operating system to be available through the MIDIAccess interface.

### Gotchas
- MIDI devices may not be detected if they are connected after the page has loaded. Use the `onstatechange` event to listen for device changes.
- MIDI messages can vary in format based on the device; familiarize yourself with MIDI specifications for proper handling.

## One Line Summary
MIDIAccess in JavaScript provides a powerful interface for web applications to connect and interact with MIDI devices, enabling creative musical applications and real-time audio manipulation.