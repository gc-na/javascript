<!--
Meta Description: # Understanding Infinity in JavaScript: Definition, Usage, and Examples ## Synopsis The `Infinity` property in JavaScript represents a numeric value t...
Meta Keywords: infinity, number, javascript, console, log
-->

# Understanding Infinity in JavaScript: Definition, Usage, and Examples

## Synopsis
The `Infinity` property in JavaScript represents a numeric value that is greater than any finite number, used primarily in calculations and comparisons involving numbers.

## Documentation
### Purpose
In JavaScript, `Infinity` is a built-in global property that indicates an overflow condition in mathematical operations. It can be utilized to represent values that exceed the maximum limit of numerical data types in JavaScript.

### Usage
The `Infinity` value is accessed directly as a property of the global object. It is important to note that `Infinity` is not a function but a constant.

```javascript
console.log(Infinity); // Outputs: Infinity
```

When used in mathematical expressions, `Infinity` behaves as expected:

- Any positive number divided by zero results in `Infinity`.
- Adding a finite number to `Infinity` still results in `Infinity`.
- Subtracting a finite number from `Infinity` still results in `Infinity`.
- Multiplying `Infinity` by any positive number remains `Infinity`.
- However, multiplying `Infinity` by zero results in `NaN` (Not-a-Number).

### Details
- **Type**: The type of `Infinity` is `number`.
- **Properties**: `Infinity` is read-only and cannot be changed or modified.
- **Comparison**: It can be compared with other numbers, where any finite number is always less than `Infinity`.

## Examples
### Basic Usage
```javascript
console.log(1 / 0); // Outputs: Infinity
console.log(Infinity + 10); // Outputs: Infinity
console.log(Infinity - 10); // Outputs: Infinity
console.log(Infinity * 2); // Outputs: Infinity
console.log(Infinity * 0); // Outputs: NaN
console.log(Math.pow(10, 1000)); // Outputs: Infinity (exceeds number range)
```

### Using Infinity in Conditions
```javascript
if (someValue === Infinity) {
    console.log("The value is infinite.");
}
```

## Explanation
### Common Pitfalls
1. **Comparisons with `-Infinity`**: It’s essential to distinguish between `Infinity` and `-Infinity` as they represent opposite ends of the number line.
   ```javascript
   console.log(Infinity > -Infinity); // Outputs: true
   ```

2. **Dividing by Zero**: Be cautious when performing operations involving division by zero, as this will result in `Infinity`, which may lead to unexpected behavior in conditional statements.

3. **NaN Result**: Remember that any operation involving `Infinity` multiplied by zero results in `NaN`. This can lead to confusion if not properly handled in calculations.

4. **String Conversion**: When converting `Infinity` to a string, it will return the string `"Infinity"`, which can be misleading if you're expecting a numeric output.

## One Line Summary
`Infinity` in JavaScript represents a numeric value greater than any finite number, crucial for handling overflow scenarios in mathematical operations.