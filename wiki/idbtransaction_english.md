<!--
Meta Description: # IDBTransaction: Managing Transactions in IndexedDB with JavaScript ## Synopsis `IDBTransaction` is a crucial interface in the IndexedDB API that all...
Meta Keywords: transaction, operations, const, data, store
-->

# IDBTransaction: Managing Transactions in IndexedDB with JavaScript

## Synopsis
`IDBTransaction` is a crucial interface in the IndexedDB API that allows developers to perform read and write operations on a database in a controlled manner, ensuring data integrity and consistency during transactions.

## Documentation
### Purpose
`IDBTransaction` is designed to manage transactions in an IndexedDB database. It provides a way to group multiple read and write operations into a single atomic transaction, ensuring that either all operations succeed or none do. This is essential in maintaining the integrity of the database, particularly in scenarios where concurrent modifications might occur.

### Usage
To create a new transaction, use the `transaction` method on an `IDBDatabase` object. The method requires two parameters:
1. **storeNames**: An array of object store names to include in the transaction.
2. **mode**: The transaction mode, which can be either `"readonly"` or `"readwrite"`.

#### Syntax
```javascript
const transaction = database.transaction(storeNames, mode);
```

### Transaction Modes
- **readonly**: Allows read operations but no modifications.
- **readwrite**: Allows both read and write operations.

### Transaction Lifecycle
Once created, a transaction can be used to perform operations on the designated object stores. The transaction will automatically commit when all operations are complete or abort if an error occurs.

### Events
`IDBTransaction` also emits several events:
- **complete**: Fired when the transaction successfully completes.
- **error**: Fired when an error occurs during the transaction.
- **abort**: Fired when the transaction is aborted.

## Examples
### Basic Usage Example
```javascript
// Open a connection to the database
const request = indexedDB.open("MyDatabase", 1);

request.onsuccess = function(event) {
    const db = event.target.result;

    // Start a readwrite transaction
    const transaction = db.transaction(["MyObjectStore"], "readwrite");

    // Access the object store
    const store = transaction.objectStore("MyObjectStore");

    // Add data to the object store
    const addRequest = store.add({ id: 1, name: "John Doe" });

    addRequest.onsuccess = function() {
        console.log("Data added successfully.");
    };

    // Handle transaction completion
    transaction.oncomplete = function() {
        console.log("Transaction completed successfully.");
    };

    // Handle transaction error
    transaction.onerror = function(event) {
        console.error("Transaction failed: ", event.target.error);
    };
};
```

### Reading Data Example
```javascript
// Opening the database connection
const request = indexedDB.open("MyDatabase");

request.onsuccess = function(event) {
    const db = event.target.result;

    // Start a readonly transaction
    const transaction = db.transaction(["MyObjectStore"], "readonly");
    const store = transaction.objectStore("MyObjectStore");

    // Get data from the object store
    const getRequest = store.get(1);

    getRequest.onsuccess = function() {
        console.log("Retrieved data: ", getRequest.result);
    };

    transaction.oncomplete = function() {
        console.log("Read transaction completed.");
    };
};
```

## Explanation
### Common Pitfalls
- **Transaction Scope**: Ensure that the transaction includes all object stores that will be accessed during the transaction. Failing to do so will result in errors.
- **Transaction Mode**: Be aware of the mode you set. Using `"readonly"` mode will prevent any write operations, which can lead to confusion when trying to update data.
- **Asynchronous Nature**: IndexedDB operations are asynchronous. Ensure that you manage your callbacks properly to avoid accessing data before it is available.

### Additional Notes
- Transactions can be nested, but the innermost transaction must complete before the outer transaction can complete.
- Avoid long-running operations inside transactions, as they may lead to degraded performance.

## One Line Summary
`IDBTransaction` is an interface in IndexedDB that allows developers to handle multiple database operations in a single, atomic transaction to ensure data integrity.