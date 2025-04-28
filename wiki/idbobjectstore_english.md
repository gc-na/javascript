<!--
Meta Description: # IDBObjectStore: A Comprehensive Guide to IndexedDB Object Stores in JavaScript ## Synopsis The `IDBObjectStore` interface is a key component of the ...
Meta Keywords: object, store, indexeddb, key, record
-->

# IDBObjectStore: A Comprehensive Guide to IndexedDB Object Stores in JavaScript

## Synopsis
The `IDBObjectStore` interface is a key component of the IndexedDB API in JavaScript, enabling developers to store and manage structured data in a transactional database within the user's browser.

## Documentation

### Purpose
`IDBObjectStore` is part of the IndexedDB API, which allows web applications to store large amounts of structured data, including files and blobs. This interface provides methods to create, read, update, and delete records in an object store.

### Usage
To use `IDBObjectStore`, you must first open a connection to an IndexedDB database and create an object store. The following steps outline how to do this:

1. **Open a Database**: Use `indexedDB.open()` to create or open a database.
2. **Create an Object Store**: In the `onupgradeneeded` event, create an object store using the `createObjectStore()` method.
3. **Perform Transactions**: Access the object store through a transaction to perform CRUD (Create, Read, Update, Delete) operations.

### Details
- **Methods**:
  - `add(value, key)`: Adds a new record to the object store.
  - `put(value, key)`: Updates an existing record or adds a new one if it doesn't already exist.
  - `get(key)`: Retrieves a record by its key.
  - `delete(key)`: Removes a record from the object store.
  - `clear()`: Deletes all records from the object store.
  - `openCursor()`: Opens a cursor for iterating over records.

- **Properties**:
  - `name`: The name of the object store.
  - `keyPath`: The key path for identifying records.
  - `autoIncrement`: Indicates whether the object store uses auto-incrementing keys.

## Examples

### Basic Usage Example
```javascript
// Open a database
const request = indexedDB.open("MyDatabase", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    // Create an object store
    const objectStore = db.createObjectStore("MyObjectStore", { keyPath: "id", autoIncrement: true });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("MyObjectStore", "readwrite");
    const objectStore = transaction.objectStore("MyObjectStore");

    // Add a record
    const record = { name: "John Doe", age: 30 };
    objectStore.add(record);

    // Get a record
    const getRequest = objectStore.get(1);
    getRequest.onsuccess = function() {
        console.log(getRequest.result);
    };
};
```

## Explanation

### Common Pitfalls
- **Versioning Issues**: Always handle the `onupgradeneeded` event properly to ensure object stores are created or updated correctly.
- **Transaction Scope**: Ensure that transactions are completed before trying to read data. Transactions that are not completed may lead to unexpected results.
- **Key Management**: Be cautious with key paths and auto-increment settings. Mismanagement can lead to duplicate keys or failed insertions.

### Gotchas
- **Asynchronous Nature**: All IndexedDB operations are asynchronous, so be sure to handle results in success callbacks to avoid attempting to access data that isn’t available yet.
- **Browser Support**: While most modern browsers support IndexedDB, always check compatibility, especially on older browsers.

## One Line Summary
`IDBObjectStore` is a vital interface in the IndexedDB API for storing and manipulating structured data in client-side databases using JavaScript.