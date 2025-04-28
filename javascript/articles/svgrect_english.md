<!--
Meta Description: # SVGRect in JavaScript: A Comprehensive Guide to Working with SVG Rectangles ## Synopsis The `SVGRect` interface in JavaScript provides a representat...
Meta Keywords: svgrect, svg, rectangle, rect, javascript
-->

# SVGRect in JavaScript: A Comprehensive Guide to Working with SVG Rectangles

## Synopsis
The `SVGRect` interface in JavaScript provides a representation of rectangles in SVG (Scalable Vector Graphics) graphics, allowing developers to create and manipulate rectangular shapes in web applications.

## Documentation
### Purpose
`SVGRect` is a part of the SVG DOM and is primarily used to define and manipulate the properties of rectangles drawn in SVG. It is commonly utilized in graphics programming, data visualization, and web design to create various visual elements.

### Usage
`SVGRect` is often utilized in conjunction with SVG elements such as `<rect>`. It provides properties and methods that allow developers to retrieve and set the dimensions and position of the rectangle.

Key properties of `SVGRect` include:
- `x`: The x-coordinate of the rectangle’s starting point.
- `y`: The y-coordinate of the rectangle’s starting point.
- `width`: The width of the rectangle.
- `height`: The height of the rectangle.

### Creating an SVGRect
`SVGRect` objects are typically created when manipulating SVG elements within the DOM, such as through the `getBBox()` method, which returns the bounding box of the SVG element as an `SVGRect`.

```javascript
const svgElement = document.querySelector('svg rect');
const rect = svgElement.getBBox(); // Returns an SVGRect object
```

## Examples
### Basic Usage Example
Here’s a simple example of how to create an SVG rectangle and access its properties using JavaScript.

```html
<svg width="200" height="200">
  <rect id="myRect" x="10" y="10" width="100" height="50" fill="blue" />
</svg>

<script>
  const rect = document.getElementById('myRect').getBBox();
  console.log(`Rectangle Position: (${rect.x}, ${rect.y})`);
  console.log(`Rectangle Dimensions: ${rect.width} x ${rect.height}`);
</script>
```

### Modifying Rectangle Properties
You can also modify the properties of the rectangle using JavaScript.

```javascript
const svgRect = document.getElementById('myRect');
svgRect.setAttribute('width', '150');
svgRect.setAttribute('height', '100');
svgRect.setAttribute('fill', 'red');
```

## Explanation
When working with `SVGRect`, developers should be aware of the following common pitfalls:

- **Coordinate System**: The coordinate system for SVG is different from the standard HTML/CSS coordinate systems. The origin (0,0) is located at the top-left corner of the SVG canvas.
- **Bounding Box**: The `getBBox()` method returns the bounding box of the SVG element as an `SVGRect`, which may not always reflect transformations applied to the element (such as rotations or scaling).
- **Style vs. Attributes**: Changing the style of an SVG rectangle via CSS does not directly affect the attributes of the rectangle. Developers must use JavaScript to update the rectangle's attributes if they want to reflect changes in the DOM.

## One Line Summary
`SVGRect` is an interface in JavaScript representing rectangles in SVG, enabling efficient manipulation of graphical elements within web applications.