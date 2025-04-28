<!--
Meta Description: # Understanding JavaScript EvalError: Definition, Usage, and Examples ## Synopsis EvalError is a built-in JavaScript error type that is thrown when an...
Meta Keywords: evalerror, error, javascript, eval, function
-->

# Understanding JavaScript EvalError: Definition, Usage, and Examples

## Synopsis
EvalError is a built-in JavaScript error type that is thrown when an error occurs during the evaluation of the `eval()` function. It is part of the global error types and is particularly useful for handling exceptions related to dynamic code evaluation.

## Documentation
### Purpose
EvalError is an error constructor in JavaScript that indicates an issue with the `eval()` function. Although it is rarely used in modern JavaScript, it serves to signify that an evaluation context has failed.

### Usage
EvalError can be instantiated directly using the `new` keyword. The constructor can take an optional message argument that describes the error.

#### Syntax
```javascript
let errorInstance = new EvalError([message]);
```

- **message (optional)**: A string that provides a description of the error.

### Properties
- **name**: Returns the name of the error (in this case, "EvalError").
- **message**: A description of the error that occurred.
- **stack**: A stack trace that provides the sequence of function calls that led to the error.

### Instance Creation
```javascript
let error = new EvalError("This is an EvalError");
console.log(error.name);    // "EvalError"
console.log(error.message); // "This is an EvalError"
```

## Examples
### Basic Example
Here is a simple example illustrating how to throw an EvalError:

```javascript
function evaluateExpression(expr) {
    if (typeof expr !== 'string') {
        throw new EvalError("Input must be a string");
    }
    return eval(expr);
}

try {
    evaluateExpression(123); // This will throw an EvalError
} catch (error) {
    if (error instanceof EvalError) {
        console.error("Caught an EvalError:", error.message);
    }
}
```

### Custom Usage
You can create a function that explicitly checks for specific evaluation conditions and throws an EvalError:

```javascript
function safeEval(expr) {
    if (!expr.includes("safe")) {
        throw new EvalError("Expression must include the word 'safe'");
    }
    return eval(expr);
}

try {
    console.log(safeEval("unsafe code")); // Throws an EvalError
} catch (error) {
    console.log(error.message); // Outputs: "Expression must include the word 'safe'"
}
```

## Explanation
### Common Pitfalls
1. **Misuse of eval()**: Using `eval()` can introduce security vulnerabilities and performance issues. It's advisable to avoid using it unless absolutely necessary.
2. **Not Catching Errors**: Failing to catch EvalErrors can lead to unhandled promise rejections or application crashes.
3. **Overusing EvalError**: As modern JavaScript rarely relies on `eval()`, EvalError might not be needed in most applications. Consider using other error types or handling mechanisms for better clarity.

### Gotchas
- **Browser Compatibility**: EvalError may behave differently across various JavaScript engines. Always check compatibility if you're targeting multiple environments.
- **Stack Trace**: The stack trace may not always provide useful debugging information, especially if the error occurs within dynamic code evaluations.

## One Line Summary
EvalError is a JavaScript error type that indicates failures during the evaluation of code strings using the `eval()` function.