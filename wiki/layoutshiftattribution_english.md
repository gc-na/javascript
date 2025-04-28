<!--
Meta Description: # Understanding LayoutShiftAttribution in JavaScript: Enhancing User Experience ## Synopsis `LayoutShiftAttribution` is a JavaScript interface that pr...
Meta Keywords: layout, user, entry, shift, shifts
-->

# Understanding LayoutShiftAttribution in JavaScript: Enhancing User Experience

## Synopsis
`LayoutShiftAttribution` is a JavaScript interface that provides detailed information about the causes of layout shifts in web applications. It is an essential part of optimizing the user experience by identifying and addressing unexpected visual changes during page rendering.

## Documentation

### Purpose
`LayoutShiftAttribution` is primarily used to improve the stability of web pages by attributing layout shifts to specific elements or actions. This is particularly useful for web developers aiming to optimize their Core Web Vitals, specifically the Cumulative Layout Shift (CLS) metric, which quantifies unexpected layout shifts that can degrade user experience.

### Usage
The `LayoutShiftAttribution` interface is typically accessed through the `LayoutShift` entry in the Performance Observer API. When a layout shift occurs, the browser generates a `LayoutShift` entry that contains a `source` property, which can be an instance of `LayoutShiftAttribution`. 

### Properties
- **source**: This property indicates the specific element that caused the layout shift.
- **hadRecentInput**: A boolean value indicating whether the layout shift was triggered by user input, such as a click or touch event.

### Accessing LayoutShiftAttribution
To utilize `LayoutShiftAttribution`, you need to set up a Performance Observer to listen for layout shifts:

```javascript
const observer = new PerformanceObserver((entryList) => {
    for (const entry of entryList.getEntries()) {
        // Accessing layout shift attribution
        if (entry.hadRecentInput) {
            console.log('Layout shift caused by user input:', entry);
        } else {
            console.log('Layout shift caused by other factors:', entry);
        }
    }
});

// Start observing layout shifts
observer.observe({ type: 'layout-shift', buffered: true });
```

## Examples

### Basic Usage Example
Here’s a simple example illustrating how to detect layout shifts and access their attribution:

```javascript
const observer = new PerformanceObserver((entries) => {
    entries.getEntries().forEach((entry) => {
        if (entry.source) {
            console.log('Shifted element:', entry.source);
            console.log('Caused by recent input:', entry.hadRecentInput);
        }
    });
});

observer.observe({ type: 'layout-shift', buffered: true });
```

### Example with User Interaction
In this example, we’ll log the layout shifts that occur due to user interactions:

```javascript
const observer = new PerformanceObserver((entries) => {
    entries.getEntries().forEach((entry) => {
        if (entry.hadRecentInput) {
            console.log('User-triggered layout shift:', entry);
        }
    });
});

observer.observe({ type: 'layout-shift', buffered: true });
```

## Explanation

### Common Pitfalls
- **Ignoring User Interaction**: Not considering whether a layout shift was caused by user interaction can lead to misunderstanding the user experience. Always check the `hadRecentInput` property.
- **Performance Overhead**: Excessive logging or processing in the observer callback can degrade performance. Keep the callback lightweight.
- **Buffering**: If you do not set `buffered: true`, you may miss earlier layout shifts that occurred before the observer was set up.

### Gotchas
- **Multiple Layout Shifts**: A single user action can cause multiple layout shifts, so ensure to aggregate or handle them appropriately.
- **Browser Support**: While `LayoutShiftAttribution` is widely supported in modern browsers, ensure to check compatibility if targeting older versions.

## One Line Summary
`LayoutShiftAttribution` in JavaScript helps developers identify the causes of layout shifts to enhance web performance and user experience.