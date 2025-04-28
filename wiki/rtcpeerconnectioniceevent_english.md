<!--
Meta Description: # RTCPeerConnectionIceEvent in JavaScript: Understanding ICE Events for WebRTC Connections ## Synopsis The `RTCPeerConnectionIceEvent` interface is a ...
Meta Keywords: candidate, ice, event, candidates, new
-->

# RTCPeerConnectionIceEvent in JavaScript: Understanding ICE Events for WebRTC Connections

## Synopsis
The `RTCPeerConnectionIceEvent` interface is a crucial component of the WebRTC API in JavaScript, facilitating real-time communication by managing the Interactive Connectivity Establishment (ICE) protocol events during peer-to-peer connections.

## Documentation
### Purpose
`RTCPeerConnectionIceEvent` is fired on an `RTCPeerConnection` instance when the ICE agent gathers a new candidate. This event is essential for establishing and maintaining a robust connection between peers in a WebRTC application.

### Usage
To utilize the `RTCPeerConnectionIceEvent`, you typically set up an event listener on an `RTCPeerConnection` object. This listener responds to `icecandidate` events, allowing developers to handle new ICE candidates as they are discovered.

### Properties
- **candidate**: This property returns an instance of `RTCIceCandidate`, which contains details about the ICE candidate that has been gathered.

### Event Handling
To listen for the `icecandidate` event:
```javascript
const peerConnection = new RTCPeerConnection();

peerConnection.onicecandidate = function(event) {
    if (event.candidate) {
        console.log('New ICE candidate:', event.candidate);
    } else {
        console.log('All ICE candidates have been sent');
    }
};
```
In this example, the event handler checks whether a new candidate has been received and logs it to the console. If no more candidates are available, it indicates that all candidates have been sent.

## Examples
### Basic Usage Example
```javascript
const peerConnection = new RTCPeerConnection();

// Listen for ICE candidate events
peerConnection.onicecandidate = function(event) {
    if (event.candidate) {
        console.log('New ICE Candidate:', event.candidate);
        // Here you can send the candidate to the remote peer
    }
};

// Create an offer to start the connection
peerConnection.createOffer()
    .then(offer => {
        return peerConnection.setLocalDescription(offer);
    })
    .catch(error => {
        console.error('Error creating offer:', error);
    });
```

### Sending ICE Candidates
When a new ICE candidate is received, you typically send it to the remote peer using a signaling server:
```javascript
peerConnection.onicecandidate = function(event) {
    if (event.candidate) {
        sendCandidateToRemotePeer(event.candidate);
    }
};
```

## Explanation
### Common Pitfalls
1. **Ignoring ICE Candidates**: Failing to handle or send ICE candidates can lead to connection failures.
2. **Assuming Connection is Instant**: The connection setup can take time; ensure you handle state changes appropriately.
3. **Not Handling `null` Candidates**: The `icecandidate` event can have a `null` candidate, indicating that all candidates have been sent. Be prepared to handle this case.

### Gotchas
- **Network Changes**: Changes in network conditions can lead to new ICE candidates being generated. Ensure your application can adapt to these changes.
- **Turn and Stun Servers**: Proper configuration of TURN and STUN servers is essential for reliable candidate gathering, especially in restrictive network environments.

## One Line Summary
`RTCPeerConnectionIceEvent` is an integral part of the WebRTC API in JavaScript, managing the lifecycle of ICE candidates for peer-to-peer connections.