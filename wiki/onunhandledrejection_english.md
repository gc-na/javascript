<!--
Meta Description: # Understanding `onunhandledrejection` in JavaScript: Handling Unhandled Promise Rejections ## Synopsis The `onunhandledrejection` event handler in Ja...
Meta Keywords: promise, event, onunhandledrejection, unhandled, rejection
-->

# Understanding `onunhandledrejection` in JavaScript: Handling Unhandled Promise Rejections

## Synopsis
The `onunhandledrejection` event handler in JavaScript is utilized to catch unhandled promise rejections globally, allowing developers to manage errors that are not explicitly handled in their promise chains.

## Documentation
### Purpose
The `onunhandledrejection` event is part of the Window interface in JavaScript. It is triggered whenever a promise is rejected and there is no `.catch()` method or other rejection handler attached to it. This feature is crucial for debugging and maintaining robust applications, as it helps in monitoring unexpected failures that may occur in asynchronous code.

### Usage
To use the `onunhandledrejection` event, you can assign a function to `window.onunhandledrejection`. This function will receive an event object containing details about the unhandled rejection, including the reason for the rejection.

### Syntax
```javascript
window.onunhandledrejection = function(event) {
    // Handle the unhandled rejection
    console.error('Unhandled promise rejection:', event.reason);
};
```

### Event Object
The event object passed to the handler includes:
- `event.reason`: The reason for the promise rejection, which can be an error object or any value that was used to reject the promise.

## Examples
### Basic Usage Example
Here’s a simple example that demonstrates how to catch unhandled promise rejections:

```javascript
// Set up the onunhandledrejection handler
window.onunhandledrejection = function(event) {
    console.error('Unhandled promise rejection:', event.reason);
};

// Create a promise that rejects without a handler
const promise = new Promise((_, reject) => {
    reject('Something went wrong!');
});

// No .catch() method is attached, so the rejection is unhandled
```

### Example with Error Handling
If you want to handle the rejection gracefully, you can log it or display an alert:

```javascript
window.onunhandledrejection = function(event) {
    alert('An error occurred: ' + event.reason);
};

// A promise that rejects
const faultyPromise = new Promise((_, reject) => {
    reject(new Error('Network error!'));
});

// No .catch() method attached
```

## Explanation
### Common Pitfalls
1. **Ignoring Rejections**: One of the most common mistakes is failing to handle promise rejections explicitly. This can lead to unhandled errors that disrupt the user experience.
2. **Multiple Handlers**: If you set `onunhandledrejection` multiple times, only the last assignment will take effect. Be mindful of reassignment when organizing your code.
3. **Async/Await**: When using async/await, unhandled rejections will also trigger the `onunhandledrejection` event. It's a good practice to wrap your async functions in try/catch blocks to handle errors directly.

### Additional Notes
- Browsers may provide warnings in the console for unhandled rejections, but relying solely on those is not a substitute for proper error handling.
- The event handler can be removed by setting `window.onunhandledrejection` to `null`.

## One Line Summary
The `onunhandledrejection` event in JavaScript allows developers to globally handle unhandled promise rejections, enhancing error management in asynchronous code.