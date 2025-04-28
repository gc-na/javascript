<!--
Meta Description: # MIDIOutput in JavaScript: A Comprehensive Guide to Web MIDI API ## Synopsis MIDIOutput is a key interface of the Web MIDI API that allows web applic...
Meta Keywords: midi, output, send, outputs, devices
-->

# MIDIOutput in JavaScript: A Comprehensive Guide to Web MIDI API

## Synopsis
MIDIOutput is a key interface of the Web MIDI API that allows web applications to send MIDI messages to connected MIDI output devices, enabling rich audio and musical interactions directly within the browser.

## Documentation

### Purpose
The MIDIOutput interface is designed to facilitate communication between web applications and MIDI output devices. This interface allows developers to send various MIDI messages, such as Note On, Note Off, Control Change, and more, effectively bridging the gap between web technologies and musical hardware.

### Usage
To utilize the MIDIOutput interface, developers must first access the Web MIDI API, which requires user permission to connect to MIDI devices. Once permission is granted, the application can enumerate available MIDI outputs and send messages to the desired device.

#### Basic Steps:
1. Request access to MIDI devices using `navigator.requestMIDIAccess()`.
2. Retrieve the list of MIDI outputs from the `MIDIAccess` object.
3. Send MIDI messages using the `send()` method of the MIDIOutput interface.

### API Reference
- **MIDIOutput.send(data, timestamp)**: Sends a MIDI message to the output device. The `data` parameter is a Uint8Array containing the MIDI message, and `timestamp` is optional, representing the time to send the message.

## Examples

### Example 1: Accessing MIDI Outputs
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const outputs = midiAccess.outputs;
    outputs.forEach((output) => {
        console.log(`Output device: ${output.name}`);
    });
}).catch((error) => {
    console.error('Could not access MIDI devices', error);
});
```

### Example 2: Sending a Note On Message
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const outputs = midiAccess.outputs;
    const output = outputs.get('Your MIDI Output ID'); // Replace with your actual device ID
    if (output) {
        const noteOnMessage = [0x90, 60, 0x7f]; // Note On for middle C with maximum velocity
        output.send(noteOnMessage);
    }
}).catch((error) => {
    console.error('Could not access MIDI devices', error);
});
```

### Example 3: Sending a Note Off Message
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const outputs = midiAccess.outputs;
    const output = outputs.get('Your MIDI Output ID'); // Replace with your actual device ID
    if (output) {
        const noteOffMessage = [0x80, 60, 0x40]; // Note Off for middle C with moderate velocity
        output.send(noteOffMessage);
    }
}).catch((error) => {
    console.error('Could not access MIDI devices', error);
});
```

## Explanation

### Common Pitfalls
- **Permission Denied**: Users must grant permission to access MIDI devices. Ensure to handle cases where permission is denied gracefully.
- **Device Availability**: Connected devices may not be available at the time of access. Always check if the output exists before attempting to send messages.
- **MIDI Message Format**: Ensure that MIDI messages are formatted correctly as Uint8Array. Invalid formats will result in messages not being sent.

### Additional Notes
- The MIDIOutput interface is supported in most modern browsers, but always verify compatibility with the target audience.
- Utilize the `send()` method judiciously, especially in performance-sensitive applications, to avoid message congestion.

## One Line Summary
MIDIOutput in JavaScript enables web applications to send MIDI messages to connected devices, enhancing interactive musical experiences.