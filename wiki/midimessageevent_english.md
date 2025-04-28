<!--
Meta Description: # MIDIMessageEvent in JavaScript: Understanding MIDI Communication in Web Applications ## Synopsis The `MIDIMessageEvent` interface in JavaScript repr...
Meta Keywords: midi, midimessageevent, event, data, messages
-->

# MIDIMessageEvent in JavaScript: Understanding MIDI Communication in Web Applications

## Synopsis
The `MIDIMessageEvent` interface in JavaScript represents an event that is dispatched when a MIDI message is received. It is a crucial part of the Web MIDI API, enabling web applications to interact with MIDI devices and handle real-time musical data.

## Documentation
### Purpose
`MIDIMessageEvent` is designed to facilitate the handling of MIDI messages in web applications. It provides developers with the ability to receive, interpret, and respond to MIDI messages from connected MIDI devices, such as synthesizers, controllers, and other musical instruments.

### Usage
To utilize `MIDIMessageEvent`, developers must first check for MIDI support in the browser. The Web MIDI API allows access to MIDI devices and the `MIDIMessageEvent` is triggered when a MIDI message is received. Here are the key properties of the `MIDIMessageEvent` interface:

- **data**: A `Uint8Array` that contains the MIDI message data.
- **receivedTime**: A double representing the time (in seconds) at which the MIDI message was received.
- **timeStamp**: A double representing the time (in milliseconds) at which the event was created.

### Example Structure
To use `MIDIMessageEvent`, you typically set up a MIDI input connection and listen for incoming messages:

```javascript
if (navigator.requestMIDIAccess) {
    navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);
}

function onMIDISuccess(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach((input) => {
        input.onmidimessage = handleMIDIMessage;
    });
}

function onMIDIFailure() {
    console.error("Could not access MIDI devices.");
}

function handleMIDIMessage(event) {
    const midiMessageEvent = event; // This is an instance of MIDIMessageEvent
    console.log(`MIDI Data: ${midiMessageEvent.data}`);
    console.log(`Received Time: ${midiMessageEvent.receivedTime}`);
}
```

## Examples
### Basic Example of Receiving MIDI Messages
Here’s a simple example demonstrating how to log incoming MIDI messages to the console:

```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const inputs = midiAccess.inputs;
    inputs.forEach((input) => {
        input.onmidimessage = (event) => {
            console.log(`MIDI Message: ${event.data}`);
        };
    });
});
```

### Example of Handling Specific MIDI Messages
In this example, we handle a specific type of MIDI message (Note On) and trigger an action:

```javascript
function handleMIDIMessage(event) {
    const [status, note, velocity] = event.data; // Destructure the MIDI data
    if (status === 144 && velocity > 0) { // Note On message
        console.log(`Note On: ${note} with velocity ${velocity}`);
    }
}
```

## Explanation
### Common Pitfalls
- **Browser Compatibility**: Not all browsers support the Web MIDI API. Ensure to check compatibility and gracefully handle the absence of support.
- **MIDI Device Permissions**: Users may need to grant permission to access MIDI devices, and this can lead to failures if not handled correctly.
- **Event Handling**: Ensure that event handlers are correctly set up to avoid missing incoming MIDI messages.

### Gotchas
- The `data` property is a `Uint8Array`, which means you may need to convert or interpret the MIDI data for specific usage.
- The timing of the received MIDI messages may not be precise, so consider this when programming real-time applications.

## One Line Summary
`MIDIMessageEvent` in JavaScript enables the handling of MIDI messages from musical devices, providing developers with essential tools for creating interactive web applications.