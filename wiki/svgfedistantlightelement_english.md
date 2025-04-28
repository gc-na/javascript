<!--
Meta Description: # SVGFEDistantLightElement: Understanding the Distant Light Filter in JavaScript ## Synopsis The `SVGFEDistantLightElement` is a key component of SVG ...
Meta Keywords: filter, svg, light, lighting, svgfedistantlightelement
-->

# SVGFEDistantLightElement: Understanding the Distant Light Filter in JavaScript

## Synopsis
The `SVGFEDistantLightElement` is a key component of SVG (Scalable Vector Graphics) filters in JavaScript, specifically designed to define distant light sources for 3D lighting effects in SVG images.

## Documentation
### Purpose
`SVGFEDistantLightElement` is part of the SVG filter effects specification and is used to create a distant light source for rendering lighting effects in SVG. It allows developers to simulate how light interacts with surfaces in a two-dimensional graphic, enhancing visual depth and realism.

### Usage
The `SVGFEDistantLightElement` is typically used within an SVG filter, specifically within an `<feDiffuseLighting>` element. This element defines how the light affects the color and brightness of the surfaces it illuminates. 

To create a distant light source, you define an `SVGFEDistantLightElement` within your SVG markup as follows:

```xml
<svg width="100" height="100">
  <defs>
    <filter id="diffuseLighting">
      <feDiffuseLighting in="SourceGraphic" surfaceScale="5">
        <feDistantLight azimuth="45" elevation="55" />
      </feDiffuseLighting>
    </filter>
  </defs>
  <rect width="100" height="100" fill="red" filter="url(#diffuseLighting)" />
</svg>
```

### Properties
- `azimuth`: Defines the direction of the light source in degrees (0 to 360). It controls the horizontal angle of the light.
- `elevation`: Sets the vertical angle of the light source in degrees (0 to 90). This affects how high the light is positioned.

## Examples
### Basic Example
Here’s a simple example demonstrating how to use `SVGFEDistantLightElement` for a basic diffuse lighting effect:

```html
<svg width="200" height="200">
  <defs>
    <filter id="lighting">
      <feDiffuseLighting in="SourceGraphic" surfaceScale="1">
        <feDistantLight azimuth="30" elevation="70" />
      </feDiffuseLighting>
    </filter>
  </defs>
  <ellipse cx="100" cy="100" rx="80" ry="50" fill="blue" filter="url(#lighting)" />
</svg>
```

### Advanced Example
In this example, we enhance the lighting effect by adjusting both azimuth and elevation for a more dramatic outcome:

```html
<svg width="300" height="300">
  <defs>
    <filter id="advancedLighting">
      <feDiffuseLighting in="SourceGraphic" surfaceScale="3">
        <feDistantLight azimuth="120" elevation="40" />
      </feDiffuseLighting>
    </filter>
  </defs>
  <circle cx="150" cy="150" r="100" fill="green" filter="url(#advancedLighting)" />
</svg>
```

## Explanation
### Common Pitfalls
- **Incorrect Angles**: Values for `azimuth` and `elevation` must be within their specified ranges. Angles outside these ranges can lead to unpredictable results.
- **Surface Scale**: The `surfaceScale` property can drastically affect the appearance of the lighting. A value of zero will result in no lighting effect, while very high values can lead to exaggerated highlights and shadows.

### Additional Notes
- The `SVGFEDistantLightElement` is only effective when used in conjunction with other filter effects, primarily `feDiffuseLighting`.
- Browser compatibility is generally good, but always check for specific SVG support if you are targeting older browsers.

## One Line Summary
`SVGFEDistantLightElement` is an SVG filter element in JavaScript that simulates distant light sources to create realistic lighting effects in graphics.