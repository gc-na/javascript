<!--
Meta Description: # Understanding the `onprogress` Event in JavaScript: A Comprehensive Guide ## Synopsis The `onprogress` event in JavaScript is an essential feature u...
Meta Keywords: event, onprogress, fetch, total, javascript
-->

# Understanding the `onprogress` Event in JavaScript: A Comprehensive Guide

## Synopsis
The `onprogress` event in JavaScript is an essential feature used to monitor the progress of data transfers, such as file uploads or downloads, providing real-time feedback to users.

## Documentation
The `onprogress` event is part of the XMLHttpRequest and Fetch API in JavaScript. It is triggered periodically during the transfer of data, allowing developers to assess the progress of operations that may take time to complete.

### Purpose
The primary purpose of the `onprogress` event is to give users visual feedback on operations, enhancing user experience by indicating how much of a task is complete.

### Usage
To use the `onprogress` event, you typically attach it to an XMLHttpRequest instance or a Fetch API call. The event handler receives an event object that contains properties such as `loaded` and `total`, which represent the number of bytes transferred and the total bytes to be transferred, respectively.

### Syntax
```javascript
xhr.onprogress = function(event) {
    // Your code here
};
```

### Properties
- `event.loaded`: The number of bytes that have been transferred.
- `event.total`: The total number of bytes to be transferred. If the total is unknown, this property will be set to `0`.

## Examples

### Example 1: Using `onprogress` with XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'path/to/your/file', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Download progress: ${percentComplete}%`);
    } else {
        console.log('Download progress: unknown bytes transferred');
    }
};

xhr.onload = function() {
    if (xhr.status === 200) {
        console.log('File downloaded successfully');
    }
};

xhr.send();
```

### Example 2: Using `onprogress` with the Fetch API
```javascript
function fetchWithProgress(url) {
    const controller = new AbortController();
    const signal = controller.signal;

    fetch(url, { signal })
        .then(response => {
            const reader = response.body.getReader();
            const contentLength = +response.headers.get('Content-Length');

            let receivedLength = 0; // Received bytes
            let chunks = []; // Array of received binary chunks (comprises the body)

            function read() {
                return reader.read().then(({ done, value }) => {
                    if (done) {
                        console.log('Fetch completed');
                        return;
                    }
                    chunks.push(value);
                    receivedLength += value.length;

                    const percentComplete = (receivedLength / contentLength) * 100;
                    console.log(`Fetch progress: ${percentComplete}%`);

                    return read(); // Recursive call
                });
            }

            return read();
        })
        .catch(error => console.error('Fetch error:', error));
}

fetchWithProgress('path/to/your/file');
```

## Explanation
### Common Pitfalls
- **Unknown Total Size**: In many cases, especially with streaming responses, the total size of the content may not be known. Always check the `lengthComputable` property before calculating progress.
- **Overusing Event Listeners**: Make sure to detach event listeners when they are no longer needed to avoid memory leaks or unintended behavior.

### Additional Notes
- The `onprogress` event is particularly useful in applications that require feedback during long-running operations, like file uploads or downloads.
- For modern applications, consider using the Fetch API, which provides a more powerful and flexible feature set compared to XMLHttpRequest.

## One Line Summary
The `onprogress` event in JavaScript enables real-time monitoring of data transfer progress, enhancing user experience during file uploads and downloads.