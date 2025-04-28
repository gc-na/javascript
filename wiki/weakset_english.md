<!--
Meta Description: # Understanding JavaScript WeakSet: A Comprehensive Guide ## Synopsis WeakSet is a built-in JavaScript object that allows you to create a collection o...
Meta Keywords: weakset, objects, object, garbage, collection
-->

# Understanding JavaScript WeakSet: A Comprehensive Guide

## Synopsis
WeakSet is a built-in JavaScript object that allows you to create a collection of objects where the references to those objects are weak. This means that if there are no other references to an object in a WeakSet, it can be garbage collected. WeakSets are particularly useful for managing memory in scenarios where you need to track objects without preventing their garbage collection.

## Documentation
### Purpose
WeakSet provides a way to store unique objects while not preventing them from being garbage collected. Unlike a regular Set, which holds strong references to its values, WeakSet only holds weak references. This is beneficial in scenarios like caching or tracking DOM elements where memory management is crucial.

### Usage
To create a WeakSet, you can use the `WeakSet` constructor:

```javascript
const myWeakSet = new WeakSet();
```

### Properties and Methods
- **WeakSet.prototype.add(value)**: Adds a new object to the WeakSet. The value must be an object; otherwise, a TypeError is thrown.
- **WeakSet.prototype.delete(value)**: Removes the specified object from the WeakSet. Returns `true` if the object was successfully removed, or `false` if it was not found.
- **WeakSet.prototype.has(value)**: Returns a boolean indicating whether the specified object exists in the WeakSet.

### Limitations
- WeakSets can only store objects; primitive values like strings, numbers, or booleans are not allowed.
- WeakSets do not have a size property, nor can you iterate over them. This is because their contents can change as objects are garbage collected.

## Examples
### Basic Usage
Creating a WeakSet and adding objects:

```javascript
let obj1 = {};
let obj2 = {};
const weakSet = new WeakSet();

weakSet.add(obj1);
weakSet.add(obj2);

console.log(weakSet.has(obj1)); // true
console.log(weakSet.has(obj2)); // true

weakSet.delete(obj1);
console.log(weakSet.has(obj1)); // false
```

### Automatic Garbage Collection
Demonstrating automatic garbage collection:

```javascript
let obj = {};
const weakSet = new WeakSet();

weakSet.add(obj);
console.log(weakSet.has(obj)); // true

obj = null; // Remove reference to the object
// After some time, the garbage collector will reclaim the memory,
// and the object will no longer exist in the WeakSet.
```

## Explanation
### Common Pitfalls
- **TypeError on Non-Objects**: Attempting to add a non-object (like a string or number) will throw a TypeError.
  
  ```javascript
  const weakSet = new WeakSet();
  weakSet.add(123); // Throws TypeError
  ```

- **No Iteration or Size**: Since WeakSet does not maintain a count or allow iteration, you cannot know how many items it contains at any given time.

- **Garbage Collection Timing**: The timing of garbage collection is not deterministic. Objects may be collected at any time when there are no strong references, so relying on the existence of objects in a WeakSet can lead to unexpected behavior.

## One Line Summary
WeakSet in JavaScript is a collection type that allows for the storage of unique objects with weak references, enabling efficient memory management by allowing garbage collection of objects without strong references.