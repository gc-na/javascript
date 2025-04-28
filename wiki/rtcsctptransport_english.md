<!--
Meta Description: # RTCSctpTransport: Understanding SCTP Transport in WebRTC with JavaScript ## Synopsis RTCSctpTransport is a WebRTC API interface that facilitates the...
Meta Keywords: sctp, data, state, rtcsctptransport, transport
-->

# RTCSctpTransport: Understanding SCTP Transport in WebRTC with JavaScript

## Synopsis
RTCSctpTransport is a WebRTC API interface that facilitates the use of the Stream Control Transmission Protocol (SCTP) for transmitting data over peer-to-peer connections. It is designed to work seamlessly within the context of WebRTC data channels, enabling reliable and unordered delivery of messages.

## Documentation

### Purpose
RTCSctpTransport is part of the WebRTC framework, which allows web applications to establish peer-to-peer connections for real-time communication. SCTP provides a reliable transport mechanism that is beneficial for applications requiring data transmission alongside audio and video streams.

### Usage
RTCSctpTransport is not instantiated directly by developers. Instead, it is created as part of the RTCPeerConnection when a data channel is established. To use SCTP, you typically define a data channel using the `createDataChannel` method of the RTCPeerConnection instance, which then utilizes RTCSctpTransport under the hood.

### Properties and Methods
- **state**: Reflects the current state of the SCTP transport (e.g., "connecting", "connected", "closed").
- **maxMessageSize**: Indicates the maximum size of messages that can be sent over the SCTP connection.
- **onstatechange**: An event handler that is called when the state of the SCTP transport changes.
  
To access the RTCSctpTransport associated with a data channel, you can use the `sctp` property of the `RTCDataChannel` instance.

## Examples

### Creating a Data Channel with SCTP
```javascript
// Create a new RTCPeerConnection
const peerConnection = new RTCPeerConnection();

// Create a data channel
const dataChannel = peerConnection.createDataChannel("myDataChannel");

// Check SCTP transport information
const sctpTransport = dataChannel.sctp;
console.log(`SCTP State: ${sctpTransport.state}`);
console.log(`Max Message Size: ${sctpTransport.maxMessageSize}`);

// Add an event listener for state changes
sctpTransport.onstatechange = () => {
    console.log(`SCTP state changed to: ${sctpTransport.state}`);
};
```

### Sending Data Over the Data Channel
```javascript
dataChannel.send("Hello, World!");
```

## Explanation
When using RTCSctpTransport, developers should be aware of the following common pitfalls:

- **State Management**: Always check the state of the SCTP transport before sending data. Attempting to send messages when the state is not "connected" can lead to errors.
  
- **Message Size Limits**: Be mindful of the `maxMessageSize` property. Sending messages larger than this limit will result in an error.

- **Event Handling**: Ensure proper handling of state changes. Using the `onstatechange` event can help manage the connection lifecycle effectively.

Additionally, SCTP's ability to support multiple streams allows for efficient data transmission without blocking audio or video data streams.

## One Line Summary
RTCSctpTransport is a WebRTC interface that enables reliable data communication over peer-to-peer connections using the SCTP protocol in JavaScript.