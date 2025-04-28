<!--
Meta Description: # Understanding FinalizationRegistry in JavaScript: A Comprehensive Guide ## Synopsis FinalizationRegistry is a JavaScript feature that allows develop...
Meta Keywords: object, garbage, finalizationregistry, callback, collected
-->

# Understanding FinalizationRegistry in JavaScript: A Comprehensive Guide

## Synopsis
FinalizationRegistry is a JavaScript feature that allows developers to register a callback function that gets invoked when an object is garbage collected, enabling the management of cleanup tasks and resource release.

## Documentation
### Purpose
The FinalizationRegistry provides a way to track and respond to the garbage collection of objects in JavaScript. This feature is particularly useful for ensuring that resources (like memory or external connections) are released when they are no longer needed, thus preventing memory leaks.

### Usage
To use a FinalizationRegistry, you need to create an instance of it by passing a callback function to its constructor. You then register a target object with the registry, along with an associated key. When the garbage collector identifies that the target object is unreachable, the callback is called with the key.

#### Syntax
```javascript
const registry = new FinalizationRegistry(callback);
registry.register(target, key);
```

### Parameters
- **callback**: A function that will be called with the key when the target object is garbage collected.
- **target**: The object to be tracked for garbage collection.
- **key**: An identifier that is passed to the callback when the target is collected.

### Example
Here's a basic example demonstrating how to use FinalizationRegistry:

```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`Object with key ${heldValue} has been garbage collected.`);
});

let obj = { name: "Example Object" };
registry.register(obj, 'exampleKey');

// Removing the reference to the object
obj = null;

// Force garbage collection (not recommended in production code)
if (typeof global.gc === 'function') {
    global.gc();
}
```

In this example, once `obj` is garbage collected, you should see `"Object with key exampleKey has been garbage collected."` logged to the console.

## Explanation
### Common Pitfalls
1. **Garbage Collection Timing**: The timing of garbage collection is not predictable. The callback may not be invoked immediately after the object becomes unreachable. Therefore, avoid relying on it for critical timing operations.

2. **Weak References**: The target object is held weakly, meaning that if no other references exist to the object, it can be collected at any time. Make sure that you manage your references carefully to avoid unexpected behavior.

3. **Callback Execution**: The callback is executed asynchronously, which might lead to issues if you expect synchronous behavior. Always design your code to handle asynchronous execution flow.

4. **Environment Support**: Ensure that the JavaScript environment supports FinalizationRegistry, as it is a relatively new feature and may not be available in older environments.

## One Line Summary
FinalizationRegistry in JavaScript allows developers to register callbacks that are invoked when objects are garbage collected, aiding in resource management and cleanup tasks.