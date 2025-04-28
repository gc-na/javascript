<!--
Meta Description: # Understanding JavaScript's `parseInt`: A Comprehensive Guide ## Synopsis The `parseInt` function in JavaScript is used to convert a string into an i...
Meta Keywords: parseint, string, javascript, console, log
-->

# Understanding JavaScript's `parseInt`: A Comprehensive Guide

## Synopsis
The `parseInt` function in JavaScript is used to convert a string into an integer, allowing developers to parse numbers from strings with various bases.

## Documentation

### Purpose
`parseInt` is a built-in JavaScript function designed to convert a string representation of a number into an integer. It can also handle different numeral systems, making it versatile for various applications.

### Usage
The syntax for `parseInt` is as follows:

```javascript
parseInt(string, radix);
```

- **string**: The string to be parsed as an integer. If the first character cannot be converted to a number, `parseInt` returns `NaN`.
- **radix**: An optional parameter that specifies the base of the numeral system (between 2 and 36) to be used for parsing the string. If omitted, the function may assume a base of 10 unless the string starts with "0x" (indicating hexadecimal).

### Details
- If the string begins with whitespace, `parseInt` ignores it.
- The function parses the string until it encounters a character that is not valid for the specified radix.
- If the string starts with a non-numeric character, it will return `NaN`.

## Examples

### Basic Usage
```javascript
console.log(parseInt("123"));       // Output: 123
console.log(parseInt("123abc"));    // Output: 123
console.log(parseInt("abc123"));    // Output: NaN
console.log(parseInt("10", 2));     // Output: 2 (binary)
console.log(parseInt("1A", 16));    // Output: 26 (hexadecimal)
```

### Handling Different Radices
```javascript
console.log(parseInt("10", 8));     // Output: 8 (octal)
console.log(parseInt("100", 10));    // Output: 100 (decimal)
console.log(parseInt("Z", 36));      // Output: 35 (base-36)
```

## Explanation
While `parseInt` is a straightforward function, there are some common pitfalls to be aware of:

1. **Radix Omission**: If the radix is omitted and the string starts with "0", `parseInt` may parse it as octal in some older implementations (though this behavior is deprecated in modern JavaScript). It’s always best practice to specify the radix explicitly.

2. **NaN Handling**: When parsing fails (e.g., when the string starts with non-numeric characters), `NaN` is returned. This can lead to unexpected behavior in calculations unless properly checked.

3. **Precision Issues**: `parseInt` only returns integers. For decimal values, consider using `parseFloat` instead.

4. **Whitespace Ignorance**: Leading whitespace is ignored, but trailing characters after a valid number are not parsed, so ensure the string is formatted correctly.

## One Line Summary
`parseInt` is a JavaScript function that converts strings into integers with optional base specification, making it essential for numeric data parsing.