<!--
Meta Description: # JavaScript CanvasPattern: Create Reusable Patterns for HTML5 Canvas ## Synopsis The `CanvasPattern` interface in JavaScript allows developers to cre...
Meta Keywords: pattern, canvas, image, create, repeat
-->

# JavaScript CanvasPattern: Create Reusable Patterns for HTML5 Canvas

## Synopsis
The `CanvasPattern` interface in JavaScript allows developers to create reusable bitmap patterns that can be used to fill shapes in the HTML5 `<canvas>` element, offering a versatile way to enhance graphics with textures and images.

## Documentation
### Purpose
`CanvasPattern` is utilized in the HTML5 Canvas API to define a pattern based on an image or another canvas. This pattern can then be applied to shapes drawn on the canvas, allowing for intricate designs and textures.

### Usage
To create a `CanvasPattern`, you first need to create a `CanvasRenderingContext2D` object from a `<canvas>` element. Then, you can use the `createPattern()` method, passing in an image (or another canvas) and a repeat style. The repeat style can be `'repeat'`, `'repeat-x'`, `'repeat-y'`, or `'no-repeat'`.

### Details
- **Method**: `createPattern(image, repetition)`
  - **Parameters**:
    - `image`: This can be an `HTMLImageElement`, `HTMLCanvasElement`, or `HTMLVideoElement`. It defines the source of the pattern.
    - `repetition`: A string that defines how the pattern should be repeated.
  - **Returns**: A `CanvasPattern` object if successful, or `null` if the pattern could not be created.

### Example
```javascript
// Get the canvas element and context
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// Create an image object
const img = new Image();
img.src = 'path/to/your/image.png';

// Draw the image pattern once it loads
img.onload = function() {
    // Create a pattern
    const pattern = ctx.createPattern(img, 'repeat');

    // Use the pattern to fill a rectangle
    ctx.fillStyle = pattern;
    ctx.fillRect(0, 0, canvas.width, canvas.height);
};
```

## Explanation
### Common Pitfalls
- **Image Loading**: Since image loading is asynchronous, ensure that you only create a pattern after the image has fully loaded to avoid getting a `null` pattern.
- **Canvas Size**: The size of the pattern is determined by the dimensions of the image or canvas passed to `createPattern()`. Make sure the dimensions fit your design requirements.
- **Memory Management**: Overusing patterns can lead to increased memory usage, especially if many patterns are created without being disposed of. Consider reusing patterns where possible.

### Gotchas
- **Cross-Origin Images**: If you attempt to use an image from a different origin without appropriate CORS headers, the pattern creation will fail due to security restrictions.
- **State Reset**: Calling `ctx.fillStyle` with a new value will override the current pattern. Ensure to store the pattern if you need to use it multiple times.

## One Line Summary
`CanvasPattern` in JavaScript allows for the creation of reusable patterns from images or canvases for enhanced graphics rendering in the HTML5 canvas.