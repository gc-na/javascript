<!--
Meta Description: # Understanding ReferenceError in JavaScript: Causes, Usage, and Solutions ## Synopsis In JavaScript, a `ReferenceError` is an error that occurs when ...
Meta Keywords: referenceerror, variable, javascript, not, scope
-->

# Understanding ReferenceError in JavaScript: Causes, Usage, and Solutions

## Synopsis
In JavaScript, a `ReferenceError` is an error that occurs when a code references a variable that has not been declared or is out of scope. This article covers the purpose, usage, common pitfalls, and examples of `ReferenceError`.

## Documentation
### Purpose
`ReferenceError` is a built-in error type in JavaScript that helps developers identify problems related to variable accessibility within their code. It typically indicates that the code is trying to access a variable that is not defined in the current scope.

### Usage
When JavaScript encounters an undeclared variable, it throws a `ReferenceError`. This helps developers debug their code by pinpointing where they have made mistakes related to variable definitions and scope.

### Details
`ReferenceError` can be triggered in various situations:
- Accessing a variable that has not been declared.
- Trying to use a variable before it has been defined.
- Accessing a property on an undefined object.

Developers can catch this error using `try...catch` statements to handle exceptions gracefully.

## Examples
### Example 1: Undeclared Variable
```javascript
console.log(myVar); // ReferenceError: myVar is not defined
```

### Example 2: Out of Scope
```javascript
function myFunction() {
    let localVar = 'I am local';
}
console.log(localVar); // ReferenceError: localVar is not defined
```

### Example 3: Using a Variable Before Declaration
```javascript
console.log(myOtherVar); // ReferenceError: myOtherVar is not defined
var myOtherVar = 10;
```

### Example 4: Accessing Property of an Undefined Object
```javascript
let obj;
console.log(obj.property); // ReferenceError: Cannot read properties of undefined (reading 'property')
```

## Explanation
Common pitfalls that lead to `ReferenceError` include:
- **Misspelling Variable Names**: Ensure that variable names are spelled correctly.
- **Scope Issues**: Be aware of variable scope. Variables declared inside functions are not accessible outside.
- **Temporal Dead Zone**: Variables declared with `let` and `const` are in a "temporal dead zone" from the start of the block until the declaration is reached, leading to a `ReferenceError` if accessed before declaration.

To avoid `ReferenceError`, always declare variables using `var`, `let`, or `const` before using them. Additionally, utilize tools like linters to catch undeclared variables during development.

## One Line Summary
A `ReferenceError` in JavaScript indicates that a variable is being accessed before it has been declared or is out of scope.