<!--
Meta Description: # Understanding CSSNumericValue in JavaScript: A Comprehensive Guide ## Synopsis The `CSSNumericValue` interface in JavaScript provides a way to work ...
Meta Keywords: css, cssnumericvalue, unit, javascript, values
-->

# Understanding CSSNumericValue in JavaScript: A Comprehensive Guide

## Synopsis
The `CSSNumericValue` interface in JavaScript provides a way to work with CSS numeric values, allowing developers to manipulate and interact with CSS units and values in a structured manner.

## Documentation
### Purpose
The `CSSNumericValue` interface is part of the CSS Typed OM (Object Model), which aims to enhance performance and ease of use when dealing with CSS values in JavaScript. It allows developers to create, manipulate, and convert CSS numeric values and units without the need for string parsing.

### Usage
`CSSNumericValue` is primarily used in conjunction with CSS functions like `CSS.unit()` and `CSS.number()`, which create numeric values and units that can be easily manipulated in JavaScript. This interface helps in managing complex CSS calculations programmatically.

### Details
- **Creating CSSNumericValue**: Use the `CSS` constructor to create instances of `CSSNumericValue`.
- **Methods**: Common methods include `add()`, `subtract()`, `multiply()`, and `divide()`, which allow arithmetic operations on numeric values.
- **Units**: Supports various CSS units like `px`, `em`, `rem`, `%`, etc., ensuring that operations respect unit conversions.

### Syntax
```javascript
const numericValue = CSS.unit(value, unit);
```
Where `value` is a number and `unit` is a string denoting the CSS unit.

## Examples
### Example 1: Creating a CSSNumericValue
```javascript
const width = CSS.unit(100, 'px');
console.log(width); // CSSNumericValue representing 100 pixels
```

### Example 2: Adding Two CSSNumericValues
```javascript
const value1 = CSS.unit(50, 'px');
const value2 = CSS.unit(25, 'px');
const total = value1.add(value2);
console.log(total); // CSSNumericValue representing 75 pixels
```

### Example 3: Multiplying a CSSNumericValue
```javascript
const value = CSS.unit(10, 'em');
const multipliedValue = value.multiply(2);
console.log(multipliedValue); // CSSNumericValue representing 20 em
```

## Explanation
### Common Pitfalls
- **Unit Mismatch**: When performing arithmetic operations, ensure that the units are compatible. For instance, adding `px` to `em` can lead to unexpected results.
- **Browser Support**: As of October 2023, not all browsers support the CSS Typed OM. Always check compatibility before using `CSSNumericValue` in production environments.

### Gotchas
- **Immutable Nature**: Instances of `CSSNumericValue` are immutable. This means that operations like `add()` or `multiply()` return a new `CSSNumericValue` rather than modifying the original instance.
- **Type Checking**: Ensure that the values being passed to methods are of the correct type to avoid runtime errors.

## One Line Summary
`CSSNumericValue` in JavaScript is an interface for efficiently working with and manipulating CSS numeric values and units.