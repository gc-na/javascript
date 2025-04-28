<!--
Meta Description: # Understanding the `onpageshow` Event in JavaScript ## Synopsis The `onpageshow` event in JavaScript is triggered when a page is shown in the browser...
Meta Keywords: event, page, when, onpageshow, loaded
-->

# Understanding the `onpageshow` Event in JavaScript

## Synopsis
The `onpageshow` event in JavaScript is triggered when a page is shown in the browser, providing a mechanism to execute scripts when the user navigates back to a page or when the page is loaded from cache.

## Documentation
The `onpageshow` event is part of the Window interface and is primarily used in web applications to handle scenarios where a page might be displayed from the cache or after a user navigates back in their browser history. This event can be particularly useful for restoring the state of UI components or reinitializing data that may have changed during the user's session.

### Purpose
- To detect when a page is shown in the browser.
- To execute specific code when the user navigates back to a cached page.

### Usage
The `onpageshow` event can be added directly to the `window` object or through an HTML element:

```javascript
window.onpageshow = function(event) {
    // Code to execute when the page is shown
    console.log("Page is shown");
};
```

Alternatively, you can use `addEventListener` to listen for the event:

```javascript
window.addEventListener('pageshow', function(event) {
    // Code to execute when the page is shown
    console.log("Page is shown with event:", event);
});
```

### Event Properties
The `pageshow` event includes the following properties:
- `persisted`: A boolean that indicates whether the page was loaded from the cache. If true, the page was loaded from the cache, and you may want to refresh certain data or reset components.

## Examples

### Example 1: Basic Usage
```javascript
window.addEventListener('pageshow', function(event) {
    if (event.persisted) {
        console.log("This page was loaded from the cache.");
    } else {
        console.log("This page was loaded normally.");
    }
});
```

### Example 2: Restoring State
```javascript
let formData = {};

window.addEventListener('pageshow', function(event) {
    if (event.persisted) {
        // Restore form state if the page was loaded from cache
        document.getElementById('myForm').value = formData.value;
    }
});

document.getElementById('myForm').addEventListener('input', function() {
    formData.value = this.value; // Save current input value
});
```

## Explanation
### Common Pitfalls
- **Not Handling Cached Pages**: If you do not check the `persisted` property, your scripts may not behave as expected when the user navigates back to a cached version of your page.
- **Event Listener Redundancy**: Adding multiple listeners for the same event can lead to performance issues. Ensure you manage your listeners appropriately to prevent duplicate executions.

### Additional Notes
- The `onpageshow` event is particularly useful in single-page applications (SPAs) where state management is crucial.
- Unlike `onload`, which only fires when the entire page is loaded for the first time, `onpageshow` allows for handling scenarios where users return to a page that may have been previously loaded.

## One Line Summary
The `onpageshow` event in JavaScript allows developers to execute code when a page is displayed, especially useful for handling cached pages and restoring state.