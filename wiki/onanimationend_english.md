<!--
Meta Description: # Understanding the `onanimationend` Event in JavaScript: A Complete Guide ## Synopsis The `onanimationend` event in JavaScript is an essential featur...
Meta Keywords: event, animation, onanimationend, css, element
-->

# Understanding the `onanimationend` Event in JavaScript: A Complete Guide

## Synopsis
The `onanimationend` event in JavaScript is an essential feature that allows developers to execute code when a CSS animation has completed. This event is part of the Animation API and is widely used to enhance user experiences through dynamic and interactive web applications.

## Documentation

### Purpose
The `onanimationend` event is triggered when a CSS animation finishes executing. It helps developers manage animations efficiently, allowing for actions such as resetting styles, triggering other animations, or executing callback functions once the animation concludes.

### Usage
The `onanimationend` event can be assigned as a property of an HTML element in JavaScript or used with event listeners. It can be applied to any element that has an associated CSS animation defined via the `@keyframes` rule.

### Syntax
```javascript
element.onanimationend = function(event) {
    // Your code here
};
```

Alternatively, using `addEventListener`:
```javascript
element.addEventListener('animationend', function(event) {
    // Your code here
});
```

### Properties of the Event Object
The `event` object passed to the `onanimationend` callback contains useful properties:
- `animationName`: The name of the animation that ended.
- `elapsedTime`: The duration (in seconds) the animation was running before it ended.
- `target`: The element that triggered the event.

## Examples

### Basic Usage Example
```html
<div id="animatedBox" style="width:100px; height:100px; background-color:red; animation: myAnimation 2s;">
</div>

<style>
@keyframes myAnimation {
    from { transform: translateX(0); }
    to { transform: translateX(100px); }
}
</style>

<script>
const box = document.getElementById('animatedBox');

box.onanimationend = function(event) {
    console.log('Animation ended:', event.animationName);
    box.style.backgroundColor = 'green'; // Change color after animation ends
};
</script>
```

### Using `addEventListener`
```html
<div id="animatedCircle" style="width:100px; height:100px; border-radius:50%; background-color:blue; animation: circleAnimation 3s;">
</div>

<style>
@keyframes circleAnimation {
    from { transform: scale(1); }
    to { transform: scale(1.5); }
}
</style>

<script>
const circle = document.getElementById('animatedCircle');

circle.addEventListener('animationend', function(event) {
    alert('Circle animation has finished.');
});
</script>
```

## Explanation

### Common Pitfalls
- **Multiple Animations**: If an element has multiple animations, the `onanimationend` event will trigger for each animation completing. Developers should check the `animationName` property to determine which animation has ended.
- **Browser Compatibility**: Ensure that the property names and event listeners are supported in the targeted browsers. Most modern browsers support `onanimationend`, but older versions may not.
- **CSS Issues**: If the CSS animation is not defined correctly or is interrupted, the `onanimationend` event may not trigger as expected.

### Additional Notes
- The `onanimationend` event is part of a broader set of animation events, including `onanimationstart` and `onanimationiteration`, which can provide more control over animation sequences.
- It's important to remember that animations defined in CSS using `@keyframes` must be applied to an element before the `onanimationend` event can be triggered.

## One Line Summary
The `onanimationend` event in JavaScript allows developers to respond programmatically when a CSS animation completes, enhancing interactive web applications.