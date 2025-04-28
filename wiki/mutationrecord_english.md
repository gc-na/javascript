<!--
Meta Description: # MutationRecord in JavaScript: Understanding DOM Mutation Observations ## Synopsis The `MutationRecord` interface provides a record of changes made t...
Meta Keywords: mutation, observer, mutations, mutationrecord, changes
-->

# MutationRecord in JavaScript: Understanding DOM Mutation Observations

## Synopsis
The `MutationRecord` interface provides a record of changes made to the DOM, enabling developers to track modifications such as additions, removals, and attribute changes to HTML elements.

## Documentation
### Purpose
`MutationRecord` is part of the Mutation Observers API, which allows developers to react to changes in the DOM efficiently. It helps in monitoring changes without resorting to older methods like polling or continuous event listening, providing a more performant mechanism to detect DOM mutations.

### Usage
To utilize `MutationRecord`, you first need to create a `MutationObserver` instance, which will listen for specific types of mutations in a target node. When a mutation occurs, the observer generates an array of `MutationRecord` objects detailing the changes.

### Details
A `MutationRecord` object contains the following properties:

- **type**: A string indicating the type of the mutation (`"childList"`, `"attributes"`, or `"subtree"`).
- **target**: The node that was affected by the mutation.
- **addedNodes**: A `NodeList` of nodes added to the target (only applicable for `"childList"` mutations).
- **removedNodes**: A `NodeList` of nodes removed from the target (only applicable for `"childList"` mutations).
- **previousSibling**: The previous sibling of the target node (only applicable for `"childList"` mutations).
- **nextSibling**: The next sibling of the target node (only applicable for `"childList"` mutations).
- **attributeName**: The name of the attribute that changed (only applicable for `"attributes"` mutations).
- **oldValue**: The old value of the changed attribute (if `attributeOldValue` option was set to `true` when creating the observer).

### Basic Usage Example
Here is a simple example to demonstrate how to use `MutationRecord` with a `MutationObserver`.

```javascript
// Select the target node
const targetNode = document.getElementById('myElement');

// Create a MutationObserver instance
const observer = new MutationObserver((mutationsList) => {
    for (const mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('A child node has been added or removed.');
            console.log('Added nodes:', mutation.addedNodes);
            console.log('Removed nodes:', mutation.removedNodes);
        } else if (mutation.type === 'attributes') {
            console.log(`The ${mutation.attributeName} attribute was modified.`);
            console.log('Old value:', mutation.oldValue);
        }
    }
});

// Configuration of the observer
const config = {
    childList: true,
    attributes: true,
    attributeOldValue: true
};

// Start observing the target node for configured mutations
observer.observe(targetNode, config);

// Example mutation: Add a child node
const newNode = document.createElement('div');
newNode.textContent = 'New Child';
targetNode.appendChild(newNode); // This will trigger the observer

// Example mutation: Change an attribute
targetNode.setAttribute('data-changed', 'true'); // This will also trigger the observer
```

## Explanation
### Common Pitfalls
1. **Performance Issues**: Excessive use of `MutationObserver` can lead to performance degradation, especially when monitoring large subtrees. Careful configuration and limiting the scope of observation can mitigate this.
   
2. **Observer Lifecycle**: Ensure to disconnect the observer using `observer.disconnect()` when it is no longer needed to avoid memory leaks.

3. **Handling Multiple Mutations**: The observer callback can be called multiple times for a single mutation. Always iterate through the `mutationsList` to handle all changes.

4. **Attribute Changes**: To track old attribute values, always set `attributeOldValue` to `true` in the observer configuration.

## One Line Summary
`MutationRecord` is a JavaScript interface that provides detailed information about changes to the DOM, enabling efficient observation of mutations.