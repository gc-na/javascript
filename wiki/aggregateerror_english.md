<!--
Meta Description: # Understanding AggregateError in JavaScript: A Comprehensive Guide ## Synopsis `AggregateError` is a built-in JavaScript error type that represents m...
Meta Keywords: error, errors, aggregateerror, multiple, javascript
-->

# Understanding AggregateError in JavaScript: A Comprehensive Guide

## Synopsis
`AggregateError` is a built-in JavaScript error type that represents multiple errors wrapped in a single object. It is particularly useful when dealing with asynchronous operations that may fail simultaneously, allowing developers to handle multiple errors in a structured manner.

## Documentation
### Purpose
`AggregateError` is designed to handle situations where multiple errors occur, especially in asynchronous contexts like `Promise.all()` or other promise-based operations. This allows developers to catch and process all errors in a unified way without losing any information about the individual errors.

### Usage
`AggregateError` is instantiated with an array of error instances. It can be thrown in any part of the code where multiple errors need to be reported together.

#### Syntax
```javascript
new AggregateError(errors, message);
```
- `errors`: An iterable of error objects.
- `message`: (Optional) A string that describes the error.

### Properties
- `name`: Returns the string "AggregateError".
- `errors`: An array containing the individual error instances.

## Examples

### Basic Usage Example
Here's a simple example of how to use `AggregateError` when handling multiple promise rejections:

```javascript
async function fetchData() {
    const promise1 = Promise.reject(new Error("Error fetching data from API 1"));
    const promise2 = Promise.reject(new Error("Error fetching data from API 2"));

    try {
        await Promise.all([promise1, promise2]);
    } catch (error) {
        if (error instanceof AggregateError) {
            console.error("Multiple errors occurred:");
            error.errors.forEach(err => console.error(err.message));
        } else {
            console.error("An unexpected error occurred:", error);
        }
    }
}

fetchData();
```

### Custom AggregateError Example
You can manually throw an `AggregateError` to group multiple errors as follows:

```javascript
function validateInputs(inputs) {
    const errors = [];
    
    inputs.forEach((input, index) => {
        if (!input) {
            errors.push(new Error(`Input at index ${index} is invalid`));
        }
    });
    
    if (errors.length > 0) {
        throw new AggregateError(errors, "Input validation failed");
    }
}

try {
    validateInputs([null, "valid", "", "valid"]);
} catch (error) {
    if (error instanceof AggregateError) {
        console.error(error.message);
        error.errors.forEach(err => console.error(err.message));
    }
}
```

## Explanation
### Common Pitfalls
- **Not Checking for AggregateError**: When catching errors from asynchronous operations, ensure you check if the caught error is an instance of `AggregateError` to appropriately handle multiple errors.
  
- **Ignoring the `message` Parameter**: While the `message` parameter is optional, providing a meaningful description can help in debugging and logging.

- **Array of Errors**: The `errors` property should be an iterable of error objects. If you pass non-error objects, it may lead to confusion when handling the errors later.

### Additional Notes
- `AggregateError` was introduced in ECMAScript 2021 (ES12), so ensure your environment supports it if you are targeting older browsers or JavaScript engines.

- Use `AggregateError` when you expect that multiple operations may fail, like network calls, to enhance the robustness of your error handling.

## One Line Summary
`AggregateError` is a JavaScript error type used to encapsulate multiple errors in a single object, enabling developers to handle multiple asynchronous errors efficiently.