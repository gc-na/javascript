<!--
Meta Description: # SVGFEFuncRElement in JavaScript: A Comprehensive Guide ## Synopsis `SVGFEFuncRElement` is an interface in the SVG (Scalable Vector Graphics) specifi...
Meta Keywords: svg, filter, svgfefuncrelement, effects, element
-->

# SVGFEFuncRElement in JavaScript: A Comprehensive Guide

## Synopsis
`SVGFEFuncRElement` is an interface in the SVG (Scalable Vector Graphics) specification that represents the `<feFuncR>` element, which is used to define the red component of color effects in filter operations. This element is crucial for manipulating colors in SVG graphics through JavaScript.

## Documentation
### Purpose
The `SVGFEFuncRElement` interface is part of the SVG filter effects module. It allows developers to specify how the red channel of an input image is processed when applying color effects such as color matrix transformations or component transfer functions.

### Usage
The `<feFuncR>` element is typically used within a `<filter>` element in SVG. It is used in conjunction with other filter primitives to create complex visual effects. The `SVGFEFuncRElement` interface is primarily used when working with JavaScript to create dynamic and interactive SVG graphics.

### Properties and Methods
`SVGFEFuncRElement` inherits from `SVGComponentTransferFunctionElement`, which provides several properties and methods to manipulate the red component of an SVG filter:

- **type**: A string that specifies the type of transfer function (e.g., "identity", "table", "discrete", "linear", "gamma").
- **tableValues**: A list of values for the transfer function when the type is set to "table".
- **slope**: A numerical value for the slope of the linear transfer function.
- **intercept**: A numerical value for the intercept of the linear transfer function.
- **amplitude**: A numerical value that defines the amplitude for gamma correction.
- **exponent**: A numerical value that defines the exponent for gamma correction.

### Example
Below is a basic example demonstrating how to use `SVGFEFuncRElement` in an SVG filter:

```html
<svg width="200" height="200">
  <defs>
    <filter id="colorFilter">
      <feColorMatrix type="matrix" values="1 0 0 0 0
                                           0 1 0 0 0
                                           0 0 1 0 0
                                           0 0 0 1 0" />
      <feComponentTransfer>
        <feFuncR type="linear" slope="1.5" intercept="0"/>
      </feComponentTransfer>
    </filter>
  </defs>
  <rect x="10" y="10" width="180" height="180" fill="blue" filter="url(#colorFilter)"/>
</svg>
```

### Explanation
When using `SVGFEFuncRElement`, keep in mind the following common pitfalls:

- **Element Nesting**: Make sure that `<feFuncR>` is properly nested within an `<feComponentTransfer>` element.
- **Component Interaction**: The effects of `feFuncR` may interact with other components in your filter. Pay attention to the order of filter primitives as they can significantly alter the output.
- **Browser Support**: While most modern browsers support SVG and its filter effects, always check for compatibility, especially on older browsers or mobile devices.

## One Line Summary
`SVGFEFuncRElement` is an SVG interface used to manipulate the red component of color effects in SVG filters through JavaScript.