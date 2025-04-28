<!--
Meta Description: # Understanding the `onanimationiteration` Event in JavaScript ## Synopsis The `onanimationiteration` event in JavaScript is triggered when a CSS anim...
Meta Keywords: event, animation, onanimationiteration, javascript, iteration
-->

# Understanding the `onanimationiteration` Event in JavaScript

## Synopsis
The `onanimationiteration` event in JavaScript is triggered when a CSS animation completes one cycle (iteration). This event is essential for developers who want to execute actions at each point of an animation loop, enhancing interactivity and user experience on web pages.

## Documentation
### Purpose
The `onanimationiteration` event is part of the CSS Animation events interface, designed to provide a mechanism for JavaScript code to respond to the completion of an animation cycle. It allows developers to handle scenarios where an action is required after each iteration of an animation, such as updating UI elements, triggering sound effects, or changing styles dynamically.

### Usage
You can attach the `onanimationiteration` event listener to any DOM element that has CSS animations applied to it. It can be done either through HTML attributes or JavaScript methods.

**JavaScript Syntax:**
```javascript
element.onanimationiteration = function(event) {
    // Code to execute on animation iteration
};
```

### Event Properties
- **Event Target**: The element that has the animation applied.
- **Animation Name**: The name of the animation that triggered the event (accessible via `event.animationName`).
- **Elapsed Time**: The time elapsed during the iteration (accessible via `event.elapsedTime`).

## Examples

### Basic Example
Here’s a simple implementation of an `onanimationiteration` event listener:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animation Iteration Example</title>
    <style>
        .animate {
            animation: spin 2s infinite;
        }

        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <div class="animate" id="animatedElement">I spin!</div>
    <script>
        const animatedElement = document.getElementById('animatedElement');

        animatedElement.onanimationiteration = function(event) {
            console.log('Animation iteration completed: ' + event.animationName);
        };
    </script>
</body>
</html>
```

### Example with Multiple Animations
If your element uses multiple animations, you can differentiate actions based on the animation name:

```javascript
animatedElement.onanimationiteration = function(event) {
    if (event.animationName === 'spin') {
        console.log('Spin animation completed.');
    } else if (event.animationName === 'fade') {
        console.log('Fade animation completed.');
    }
};
```

## Explanation
### Common Pitfalls
1. **Animation Not Triggering the Event**: Ensure that the CSS animations are correctly defined and applied to the element. The `onanimationiteration` event will only fire if the animation plays through at least once.
2. **Multiple Animations**: If multiple animations are applied, the `onanimationiteration` event will trigger for each animation. Ensure you handle each animation case in your event handler to avoid confusion.
3. **Browser Compatibility**: While most modern browsers support the `onanimationiteration` event, it’s always good practice to check for compatibility if you are targeting older browsers.

### Additional Notes
- The `onanimationiteration` event can be combined with other animation events like `onanimationstart` and `onanimationend` to create comprehensive animation handling in JavaScript.
- Consider performance implications when executing complex operations within the event handler, as it can affect animation fluidity.

## One Line Summary
The `onanimationiteration` event in JavaScript allows developers to execute specific actions whenever a CSS animation completes one cycle.