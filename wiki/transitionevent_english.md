<!--
Meta Description: # TransitionEvent in JavaScript: Understanding CSS Transitions ## Synopsis The `TransitionEvent` interface in JavaScript represents events that occur ...
Meta Keywords: transition, event, css, transitionevent, when
-->

# TransitionEvent in JavaScript: Understanding CSS Transitions

## Synopsis
The `TransitionEvent` interface in JavaScript represents events that occur when a CSS transition starts, ends, or is interrupted. It provides developers with a way to respond to changes in the state of a CSS transition.

## Documentation

### Purpose
The `TransitionEvent` is part of the Web API that helps developers handle events triggered by CSS transitions. When a CSS property changes from one value to another over a specified duration, the `TransitionEvent` allows you to listen for the start and completion of this transition.

### Usage
The `TransitionEvent` can be accessed using event listeners attached to DOM elements. To listen for transition events, you can use the `addEventListener` method with the event type `"transitionend"`.

### Properties
- `propertyName`: A string that contains the name of the CSS property that is transitioning.
- `elapsedTime`: A double representing the time in seconds that the transition has been running.
- `pseudoElement`: A string that indicates the pseudo-element of the CSS property (if applicable).

### Event Types
- `transitionstart`: Fired when the transition starts.
- `transitionend`: Fired when the transition completes.
- `transitioncancel`: Fired when the transition is canceled.

### Example
```javascript
// Select the element to observe for transitions
const box = document.querySelector('.box');

// Add an event listener for the transitionend event
box.addEventListener('transitionend', function(event) {
    console.log(`Transition on property: ${event.propertyName} completed in ${event.elapsedTime} seconds.`);
});

// Trigger a CSS transition by changing the style
box.style.transition = 'transform 2s';
box.style.transform = 'translateX(100px)';
```

## Explanation
When working with `TransitionEvent`, it's essential to be aware of common pitfalls:

- **Timing Issues**: Ensure that the transition properties are set before triggering the transition. If the styles are not applied correctly, the event may not fire as expected.
- **Multiple Transitions**: If an element has multiple CSS properties transitioning simultaneously, the `transitionend` event will fire for each property separately, which may require additional handling in your event listener.
- **Browser Compatibility**: While most modern browsers support `TransitionEvent`, always check compatibility to ensure that your application functions correctly across different platforms.

## One Line Summary
The `TransitionEvent` interface in JavaScript allows developers to listen for and respond to changes in CSS transitions, providing valuable insights into the state of animated properties.