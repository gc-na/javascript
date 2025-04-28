<!--
Meta Description: # BigInt in JavaScript: A Comprehensive Guide to Handling Large Integers ## Synopsis BigInt is a built-in object in JavaScript that allows developers ...
Meta Keywords: bigint, const, javascript, integers, large
-->

# BigInt in JavaScript: A Comprehensive Guide to Handling Large Integers

## Synopsis
BigInt is a built-in object in JavaScript that allows developers to represent and manipulate integers larger than the Number.MAX_SAFE_INTEGER (2^53 - 1). This feature is essential for applications that require precise computations with large integers, such as cryptography, financial calculations, and high-precision arithmetic.

## Documentation
### Purpose
BigInt was introduced in ECMAScript 2020 (ES11) to address the limitations of the Number type in JavaScript, which can safely represent integers only up to 2^53 - 1. With BigInt, developers can work with arbitrarily large integers, enabling more accurate calculations in scenarios where precision is critical.

### Usage
To create a BigInt, you can use the `BigInt` constructor or append `n` to the end of an integer literal. 

#### Syntax:
```javascript
BigInt(value);
```
or 
```javascript
valuen; // where value is an integer
```

### Details
- **Type**: BigInt is a primitive type, similar to Number, but it specifically handles large integers.
- **Operations**: BigInt supports arithmetic operations like addition, subtraction, multiplication, and division. However, be cautious as mixing BigInt and Number types in operations leads to a TypeError.
- **Comparisons**: BigInt can be compared with other BigInts using the usual comparison operators (e.g., `<`, `>`, `===`), but be wary of comparing BigInt with Number, which can yield unexpected results.

## Examples
### Creating BigInt
```javascript
const bigInt1 = BigInt(123456789012345678901234567890);
const bigInt2 = 123456789012345678901234567890n; // Using the 'n' suffix
```

### Basic Arithmetic
```javascript
const a = BigInt(10);
const b = BigInt(20);

const sum = a + b; // 30n
const difference = b - a; // 10n
const product = a * b; // 200n
const quotient = b / a; // 2n
const remainder = b % a; // 0n
```

### Comparisons
```javascript
const bigIntA = 100n;
const bigIntB = 100n;
const bigIntC = 200n;

console.log(bigIntA === bigIntB); // true
console.log(bigIntA < bigIntC); // true
```

## Explanation
### Common Pitfalls
- **Mixing Types**: Attempting to perform arithmetic operations between a BigInt and a Number will result in a TypeError. To avoid this, ensure both operands are of the same type.
  
  ```javascript
  const num = 10;
  const bigInt = 10n;

  // This will throw an error
  console.log(num + bigInt); // TypeError
  ```

- **Precision**: While BigInt can represent large integers, it cannot represent fractions or decimals. Any attempt to do so will also result in a TypeError.

- **JSON Serialization**: BigInt cannot be directly serialized to JSON. When converting an object with a BigInt property to JSON, you will need to explicitly convert it to a string.

### Additional Notes
- **Compatibility**: BigInt is supported in all modern browsers and Node.js versions from 10.4.0 onward.
- **Performance**: While BigInt allows for large integers, performance may vary depending on the operation and the size of the numbers. Profiling is recommended for performance-critical applications.

## One Line Summary
BigInt in JavaScript provides a way to work with integers larger than Number.MAX_SAFE_INTEGER, enabling high-precision arithmetic for applications requiring large integer calculations.