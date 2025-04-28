<!--
Meta Description: # onselectionchange: Understanding the Selection Change Event in JavaScript ## Synopsis The `onselectionchange` event in JavaScript is used to detect ...
Meta Keywords: selection, event, text, onselectionchange, document
-->

# onselectionchange: Understanding the Selection Change Event in JavaScript

## Synopsis
The `onselectionchange` event in JavaScript is used to detect changes in the selection of a document or a specific element, allowing developers to respond to user interactions when text or elements are selected.

## Documentation
The `onselectionchange` event is part of the Selection API in JavaScript, which provides a way to interact with the selected text or elements within a document. This event triggers whenever the selection changes, including when users select new text, deselect text, or modify existing selections.

### Purpose
The primary purpose of the `onselectionchange` event is to enable developers to execute specific actions based on user selection. This can be particularly useful in applications that require dynamic responses to user inputs, such as text editors, annotation tools, or interactive web pages.

### Usage
To use the `onselectionchange` event, you can add an event listener to the `document` or specific elements like `textarea` or `contenteditable` elements. The event listener can then call a function that processes the selection.

### Syntax
```javascript
document.addEventListener('selectionchange', function() {
    // Your code here
});
```

## Examples

### Basic Example
Here’s a simple example that logs the selected text to the console whenever the selection changes:

```javascript
document.addEventListener('selectionchange', function() {
    const selection = window.getSelection();
    console.log('Selected text:', selection.toString());
});
```

### Highlighting Selected Text
In this example, when the selection changes, the selected text will be highlighted by wrapping it in a `<span>` with a specific class:

```javascript
document.addEventListener('selectionchange', function() {
    const selection = window.getSelection();
    if (selection.rangeCount > 0) {
        const range = selection.getRangeAt(0);
        const span = document.createElement('span');
        span.className = 'highlight';
        range.surroundContents(span);
    }
});
```

## Explanation
While using the `onselectionchange` event is straightforward, there are a few common pitfalls to be aware of:

1. **Performance Concerns**: Frequent changes in selection can cause the event to fire multiple times in rapid succession. Ensure that the event handler is efficient to avoid performance issues.

2. **Browser Compatibility**: While the `onselectionchange` event is widely supported in modern browsers, always check compatibility, especially if supporting older versions.

3. **Range Management**: When modifying selections (e.g., highlighting), be careful to manage the selection ranges properly to avoid unintended side effects.

4. **Event Bubbling**: The `selectionchange` event does not bubble up the DOM. Therefore, it must be directly attached to the document or relevant elements.

## One Line Summary
The `onselectionchange` event in JavaScript allows developers to detect changes in text selection, enabling dynamic interactions based on user selections.