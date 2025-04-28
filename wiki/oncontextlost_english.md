<!--
Meta Description: # Understanding `oncontextlost` in JavaScript: Managing WebGL Context Loss ## Synopsis The `oncontextlost` event is a crucial aspect of the HTML5 canv...
Meta Keywords: context, event, webgl, lost, loss
-->

# Understanding `oncontextlost` in JavaScript: Managing WebGL Context Loss

## Synopsis
The `oncontextlost` event is a crucial aspect of the HTML5 canvas API that pertains to WebGL. It allows developers to handle the loss of a WebGL context, ensuring that applications can respond gracefully to scenarios where the rendering context is lost due to various reasons.

## Documentation
The `oncontextlost` event is triggered when the WebGL rendering context is lost. This can happen due to various reasons such as the browser switching to a different tab, resource limitations, or hardware acceleration issues. When this event occurs, the rendering state is invalidated, and all resources associated with the context must be re-created to continue rendering.

### Purpose
The primary purpose of the `oncontextlost` event is to notify developers that the WebGL context is no longer available, allowing them to implement necessary cleanup or state management procedures.

### Usage
To use the `oncontextlost` event, you need to attach an event listener to the WebGL context. This can be done as follows:

```javascript
const canvas = document.getElementById('myCanvas');
const gl = canvas.getContext('webgl');

canvas.addEventListener('webglcontextlost', function(event) {
    event.preventDefault(); // Prevent default behavior
    console.log('WebGL context lost!');
});
```

### Details
- **Event Type**: `WebGLContextEvent`
- **Event Properties**: The event does not have specific properties, but it can be used to determine whether the context has been lost and to execute cleanup code.
- **Preventing Default Behavior**: It is often recommended to call `event.preventDefault()` to prevent the default behavior of the context being lost, allowing you to handle it more gracefully.

## Examples
### Basic Example of oncontextlost Usage

```javascript
const canvas = document.getElementById('myCanvas');
const gl = canvas.getContext('webgl');

// Adding the context lost event listener
canvas.addEventListener('webglcontextlost', function(event) {
    event.preventDefault(); // Prevents the default context loss
    console.log('WebGL context lost, handling cleanup.');
    // Implement cleanup logic here
});

// Example of normal rendering setup
function render() {
    // Rendering logic here
    requestAnimationFrame(render);
}

// Start rendering
render();
```

### Handling Context Restoration

In addition to handling context loss, you might also want to manage context restoration with `oncontextrestored`.

```javascript
canvas.addEventListener('webglcontextrestored', function() {
    console.log('WebGL context restored, reinitializing resources.');
    // Reinitialize resources and rendering state
});
```

## Explanation
### Common Pitfalls
- **Forgetting to Prevent Default**: Not calling `event.preventDefault()` can lead to the loss of the context without any opportunity for cleanup.
- **Resource Management**: After a context loss, all resources such as textures and buffers need to be recreated. Failing to do this can result in graphical issues or crashes.
- **Not Handling Restoration**: If you don't listen for the `oncontextrestored` event, your application may remain in a non-functional state after the context is restored.

### Additional Notes
- The context can be lost for several reasons, including but not limited to, running out of memory. Understanding the circumstances leading to context loss can help in designing more resilient applications.
- Always test your WebGL applications in scenarios where the context may be lost, such as switching tabs or resizing windows.

## One Line Summary
The `oncontextlost` event in JavaScript is essential for managing WebGL context loss, allowing developers to implement cleanup and restoration logic for a seamless user experience.