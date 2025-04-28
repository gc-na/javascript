<!--
Meta Description: # PresentationConnectionList in JavaScript: A Guide to Handling Presentation Connections ## Synopsis The `PresentationConnectionList` interface in the...
Meta Keywords: presentation, connection, connections, presentationconnectionlist, active
-->

# PresentationConnectionList in JavaScript: A Guide to Handling Presentation Connections

## Synopsis
The `PresentationConnectionList` interface in the JavaScript Presentation API provides a list of active presentation connections, enabling developers to manage and interact with multiple connected presentation displays effectively.

## Documentation
The `PresentationConnectionList` interface is part of the Presentation API, which allows web applications to communicate with presentation displays (like smart TVs or projectors). This interface allows developers to access all currently active presentation connections, making it easier to manage and control the content displayed on connected devices.

### Purpose
The primary purpose of `PresentationConnectionList` is to provide a structured way to access and manipulate connection objects representing the active presentation sessions. Each connection can be used to send messages, manage states, and control the presentation flow.

### Usage
To access the `PresentationConnectionList`, you can use the `getConnectionList()` method from the `Presentation` interface. This method returns a `PresentationConnectionList` object containing all active connections.

```javascript
let connectionList = presentation.getConnectionList();
```

### Properties and Methods
- **length**: A read-only property that returns the number of active connections in the list.
- **item(index)**: A method that returns the `PresentationConnection` at the specified index.

## Examples
### Basic Usage Example
Here’s how to retrieve and log the active presentation connections:

```javascript
if (navigator.presentation) {
    navigator.presentation.getConnectionList().then((connectionList) => {
        console.log(`Number of active connections: ${connectionList.length}`);
        
        for (let i = 0; i < connectionList.length; i++) {
            let connection = connectionList.item(i);
            console.log(`Connection ${i}: ${connection.id}`);
        }
    }).catch((error) => {
        console.error('Error retrieving connection list:', error);
    });
}
```

### Example: Managing Connections
You can use the `PresentationConnection` objects retrieved from the `PresentationConnectionList` to manage the displayed content:

```javascript
if (navigator.presentation) {
    navigator.presentation.getConnectionList().then((connectionList) => {
        for (let i = 0; i < connectionList.length; i++) {
            let connection = connectionList.item(i);
            connection.send('Update content'); // Send a message to the presentation display
        }
    });
}
```

## Explanation
### Common Pitfalls
1. **Browser Compatibility**: Not all browsers support the Presentation API. Make sure to check for compatibility before using this feature.
2. **Connection State**: Always verify the state of the connection before attempting to send messages. If the connection is closed, attempts to send messages will fail.
3. **Error Handling**: Implement proper error handling for cases where retrieving the connection list might fail, such as when there are no connections available.

### Gotchas
- The `PresentationConnectionList` is a live list that reflects current connections, so calling `getConnectionList()` multiple times may yield different results.
- Remember that the `PresentationConnection` objects can have varying states (connecting, connected, closed), and the corresponding application logic should handle these states appropriately.

## One Line Summary
The `PresentationConnectionList` interface in JavaScript provides a way to manage and interact with active presentation connections in web applications.