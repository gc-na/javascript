<!--
Meta Description: # Understanding Symbol in JavaScript: A Comprehensive Guide ## Synopsis The `Symbol` is a unique and immutable primitive data type introduced in ECMAS...
Meta Keywords: symbol, symbols, object, not, using
-->

# Understanding Symbol in JavaScript: A Comprehensive Guide

## Synopsis
The `Symbol` is a unique and immutable primitive data type introduced in ECMAScript 2015 (ES6) that is used to create anonymous and unique values primarily for object properties.

## Documentation
### Purpose
`Symbol` serves as a way to create unique identifiers for object properties, which can help prevent naming collisions in objects. Unlike strings, symbols are not coerced into strings, making them ideal for defining properties that should not be accidentally overwritten.

### Usage
To create a symbol, use the `Symbol()` function. You can optionally pass a description as a string, which can be useful for debugging.

```javascript
const mySymbol = Symbol('description');
```

### Details
- **Uniqueness**: Every time you call `Symbol()`, a new, unique symbol is created.
- **Non-enumerable**: Symbols are not included in `for...in` loops or in `Object.keys()`, which helps keep properties hidden.
- **Global Symbols**: You can create global symbols using `Symbol.for(key)`, which allows you to retrieve the same symbol later using `Symbol.for(key)`.

## Examples
### Basic Example
```javascript
const id = Symbol('id');

const user = {
  name: 'Alice',
  [id]: 12345
};

console.log(user); // { name: 'Alice' }
console.log(user[id]); // 12345
```

### Using Global Symbols
```javascript
const globalSymbol = Symbol.for('globalKey');

const object1 = {
  [globalSymbol]: 'Object 1'
};

const object2 = {
  [globalSymbol]: 'Object 2'
};

console.log(object1[globalSymbol]); // 'Object 1'
console.log(object2[globalSymbol]); // 'Object 2'
```

## Explanation
### Common Pitfalls
- **Symbol as Property Key**: Symbols must be used as property keys using computed property names (i.e., bracket notation) since they cannot be accessed using dot notation.
- **Symbol Description**: The description provided when creating a symbol is only for debugging purposes and does not affect the symbol's uniqueness.
- **Global Namespace**: While global symbols can be shared, if you create a symbol using `Symbol('foo')` and `Symbol.for('foo')`, they will not be the same symbol.

### Gotchas
- Symbols are not string-compatible. Be cautious when using them as keys in applications where string keys are expected.
- When logging objects, symbols will not appear in the console output by default, which may lead to confusion if you're trying to debug your code.

## One Line Summary
The `Symbol` in JavaScript is a unique and immutable primitive type used to create unique identifiers for object properties, helping to avoid property name collisions.