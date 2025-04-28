<!--
Meta Description: # Understanding the oncontextrestored Event in JavaScript: An In-Depth Guide ## Synopsis The `oncontextrestored` event is an essential feature in Java...
Meta Keywords: canvas, context, event, ctx, oncontextrestored
-->

# Understanding the oncontextrestored Event in JavaScript: An In-Depth Guide

## Synopsis
The `oncontextrestored` event is an essential feature in JavaScript, particularly in the context of the HTML5 `<canvas>` element. It allows developers to handle the scenario where the rendering context of a canvas is restored after being lost, such as when the browser needs to free up resources or when the user navigates away and back. 

## Documentation
### Purpose
The `oncontextrestored` event is triggered when a lost rendering context is restored. This is particularly relevant for applications that rely heavily on the `<canvas>` for graphics rendering, including games, animations, and data visualizations. 

### Usage
To use the `oncontextrestored` event, you need to attach an event listener to the canvas element's context. This can be done using either the `addEventListener` method or by directly assigning the event handler to the `oncontextrestored` property.

### Syntax
```javascript
canvasElement.getContext('2d').oncontextrestored = function(event) {
    // Your code here
};
```
Or using `addEventListener`:
```javascript
canvasElement.getContext('2d').addEventListener('contextrestored', function(event) {
    // Your code here
});
```

## Examples
### Example 1: Simple Usage of oncontextrestored
```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');

    // Handle context restoration
    ctx.oncontextrestored = function() {
        console.log('Canvas context has been restored!');
        // Redraw your canvas content here
        ctx.fillStyle = 'blue';
        ctx.fillRect(0, 0, 400, 400);
    };

    // Simulating a context loss and restoration
    function simulateContextLoss() {
        ctx = null; // Simulate loss
        // Simulate browser restoring the context
        ctx = canvas.getContext('2d');
        ctx.dispatchEvent(new Event('contextrestored'));
    }

    // Simulate after 3 seconds
    setTimeout(simulateContextLoss, 3000);
</script>
```

### Example 2: Using addEventListener
```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');

    ctx.addEventListener('contextrestored', function() {
        console.log('Canvas context has been restored!');
        // Redraw your canvas content here
        ctx.fillStyle = 'red';
        ctx.fillRect(0, 0, 400, 400);
    });

    // Simulating context loss and restoration
    function simulateContextLoss() {
        ctx = null; // Simulate loss
        // Simulate browser restoring the context
        ctx = canvas.getContext('2d');
        ctx.dispatchEvent(new Event('contextrestored'));
    }

    // Simulate after 3 seconds
    setTimeout(simulateContextLoss, 3000);
</script>
```

## Explanation
### Common Pitfalls
1. **Context Loss**: The context can be lost for various reasons, such as resizing the browser window or switching tabs. Always ensure you handle both the `contextlost` and `contextrestored` events.
2. **Redrawing**: When the context is restored, you must redraw all necessary graphics, as the canvas state is reset.
3. **Event Handling**: Ensure that your event listener is correctly set up; otherwise, the event may not trigger as expected.

### Gotchas
- The `oncontextrestored` event will not fire if the context was never lost.
- Always check for the availability of the rendering context before attempting to draw on the canvas.

## One Line Summary
The `oncontextrestored` event in JavaScript is triggered when a canvas rendering context is restored, allowing developers to redraw graphics after a context loss.