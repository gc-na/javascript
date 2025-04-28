<!--
Meta Description: # JavaScript CanvasGradient: Creating Stunning Gradients in HTML5 Canvas ## Synopsis `CanvasGradient` is a powerful JavaScript feature that allows dev...
Meta Keywords: gradient, ctx, canvas, const, addcolorstop
-->

# JavaScript CanvasGradient: Creating Stunning Gradients in HTML5 Canvas

## Synopsis
`CanvasGradient` is a powerful JavaScript feature that allows developers to create smooth color transitions in graphics rendered on the HTML5 `<canvas>` element. This object is essential for enhancing visual aesthetics in web applications and games.

## Documentation
### Purpose
`CanvasGradient` is used to define gradient color fills for shapes drawn on an HTML5 canvas. It can create both linear and radial gradients, enabling developers to produce visually appealing effects in web graphics.

### Usage
To create a `CanvasGradient`, you first need to obtain a 2D rendering context from a `<canvas>` element. You can then create either a linear gradient using `createLinearGradient()` or a radial gradient using `createRadialGradient()`.

#### Creating a Linear Gradient
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// Define the linear gradient
const linearGradient = ctx.createLinearGradient(x0, y0, x1, y1);
linearGradient.addColorStop(0, 'color1');
linearGradient.addColorStop(1, 'color2');

// Use the gradient to fill a rectangle
ctx.fillStyle = linearGradient;
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

#### Creating a Radial Gradient
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// Define the radial gradient
const radialGradient = ctx.createRadialGradient(x0, y0, r0, x1, y1, r1);
radialGradient.addColorStop(0, 'color1');
radialGradient.addColorStop(1, 'color2');

// Use the gradient to fill a circle
ctx.fillStyle = radialGradient;
ctx.beginPath();
ctx.arc(centerX, centerY, radius, 0, Math.PI * 2);
ctx.fill();
```

### Details
- **addColorStop(offset, color)**: Adds a color stop to the gradient. The `offset` should be a value between 0 and 1, where 0 represents the start of the gradient and 1 represents the end. The `color` can be defined in various formats, such as HEX, RGB, or RGBA.
- **Parameters for createLinearGradient(x0, y0, x1, y1)**:
  - `(x0, y0)`: The starting point of the gradient.
  - `(x1, y1)`: The ending point of the gradient.
  
- **Parameters for createRadialGradient(x0, y0, r0, x1, y1, r1)**:
  - `(x0, y0)`: The center of the starting circle.
  - `r0`: The radius of the starting circle.
  - `(x1, y1)`: The center of the ending circle.
  - `r1`: The radius of the ending circle.

## Examples
### Example 1: Simple Linear Gradient
```javascript
const canvas = document.getElementById('gradientCanvas');
const ctx = canvas.getContext('2d');

const gradient = ctx.createLinearGradient(0, 0, 200, 0);
gradient.addColorStop(0, 'red');
gradient.addColorStop(1, 'blue');

ctx.fillStyle = gradient;
ctx.fillRect(0, 0, 200, 100);
```

### Example 2: Simple Radial Gradient
```javascript
const canvas = document.getElementById('radialCanvas');
const ctx = canvas.getContext('2d');

const radialGradient = ctx.createRadialGradient(100, 100, 20, 100, 100, 100);
radialGradient.addColorStop(0, 'yellow');
radialGradient.addColorStop(1, 'green');

ctx.fillStyle = radialGradient;
ctx.beginPath();
ctx.arc(100, 100, 100, 0, Math.PI * 2);
ctx.fill();
```

## Explanation
When working with `CanvasGradient`, keep in mind the following common pitfalls:
- **Color Stops**: Ensure you add color stops in the correct order; if they are not ordered properly, the gradient may not appear as expected.
- **Coordinates**: Double-check the coordinates provided for linear and radial gradients to avoid misaligned gradients.
- **Canvas Size**: The gradient may not scale correctly if the canvas size changes after the gradient is created.

## One Line Summary
`CanvasGradient` in JavaScript allows developers to create smooth and vibrant color gradients for shapes in the HTML5 canvas, enhancing visual appeal in web applications.