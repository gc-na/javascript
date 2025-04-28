<!--
Meta Description: # MIDIConnectionEvent in JavaScript: Understanding and Using MIDI Connections ## Synopsis The `MIDIConnectionEvent` interface provides information abo...
Meta Keywords: midi, event, port, type, midiconnectionevent
-->

# MIDIConnectionEvent in JavaScript: Understanding and Using MIDI Connections

## Synopsis
The `MIDIConnectionEvent` interface provides information about the connection and disconnection of MIDI devices in web applications, allowing developers to build interactive music applications that respond to MIDI device changes.

## Documentation

### Purpose
`MIDIConnectionEvent` is part of the Web MIDI API, which enables web applications to communicate with MIDI (Musical Instrument Digital Interface) devices. This interface is crucial for developers who want to handle MIDI input and output dynamically, responding to the connection status of MIDI devices in real-time.

### Usage
When a MIDI device is connected or disconnected, a `MIDIConnectionEvent` is dispatched. This event contains details such as the type of connection (input or output) and the associated MIDI device. Developers can listen for these events to update their applications accordingly.

### Properties
- **type**: A string that indicates the type of connection event (e.g., "connected" or "disconnected").
- **port**: A `MIDIPort` object that represents the MIDI port associated with the connection event.

### Event Listener
To utilize the `MIDIConnectionEvent`, developers can add an event listener to the `navigator` object, specifically for the `statechange` event:

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    midiAccess.onstatechange = function(event) {
        console.log(`MIDI ${event.port.type} port ${event.port.name} has been ${event.type}.`);
    };
});
```

## Examples

### Example 1: Listening for MIDI Device Connections
Here's a simple example showing how to listen for connections and disconnections of MIDI devices:

```javascript
navigator.requestMIDIAccess()
    .then(midiAccess => {
        midiAccess.onstatechange = event => {
            if (event.port.state === 'connected') {
                console.log(`Connected: ${event.port.name}`);
            } else {
                console.log(`Disconnected: ${event.port.name}`);
            }
        };
    })
    .catch(err => console.error('MIDI Access failed', err));
```

### Example 2: Handling Different Types of MIDI Ports
This example demonstrates how to differentiate between input and output ports when a connection event occurs:

```javascript
navigator.requestMIDIAccess()
    .then(midiAccess => {
        midiAccess.onstatechange = event => {
            if (event.port.type === 'input') {
                console.log(`MIDI Input Port: ${event.port.name} is now ${event.type}`);
            } else if (event.port.type === 'output') {
                console.log(`MIDI Output Port: ${event.port.name} is now ${event.type}`);
            }
        };
    })
    .catch(err => console.error('MIDI Access failed', err));
```

## Explanation
### Common Pitfalls
- **Browser Support**: Ensure the browser supports the Web MIDI API. As of October 2023, support varies; check compatibility before implementation.
- **Permissions**: Users may need to grant permissions for MIDI devices to be accessed. Handle permission errors gracefully.
- **Event Handling**: Be careful with the state of your application during connection events—ensure your UI reflects the current state of MIDI devices.

### Additional Notes
- The `MIDIConnectionEvent` is fired whenever a MIDI device is added or removed. This makes it essential for applications that require real-time interaction with MIDI hardware.
- Keep in mind that the Web MIDI API is designed for use in web applications, and using it in non-browser environments may not work as expected.

## One Line Summary
`MIDIConnectionEvent` allows web applications to handle real-time changes in MIDI device connections, enhancing interactive music experiences.