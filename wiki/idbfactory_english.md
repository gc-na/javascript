<!--
Meta Description: # IDBFactory: A Comprehensive Guide to IndexedDB in JavaScript ## Synopsis The `IDBFactory` interface provides a way to interact with IndexedDB, a low...
Meta Keywords: database, indexeddb, event, idbfactory, data
-->

# IDBFactory: A Comprehensive Guide to IndexedDB in JavaScript

## Synopsis
The `IDBFactory` interface provides a way to interact with IndexedDB, a low-level API for client-side storage of significant amounts of structured data, including files/blobs. It allows developers to create, open, and delete databases using JavaScript.

## Documentation
### Purpose
`IDBFactory` is part of the IndexedDB API, which is designed to store large amounts of data in a transactional way. It allows web applications to store data persistently and access it on subsequent visits, providing offline capabilities and enhanced performance.

### Usage
The primary methods of the `IDBFactory` interface include:
- `open()`: This method creates a new database or opens an existing one.
- `deleteDatabase()`: This method deletes a specified database.

### Method Descriptions
1. **open(name, version)**: 
   - **Parameters**:
     - `name` (String): The name of the database.
     - `version` (Number): The version number of the database. If the database does not exist, it will be created with this version.
   - **Returns**: An `IDBOpenDBRequest` object which can be used to handle the success or error of the operation.

2. **deleteDatabase(name)**: 
   - **Parameters**:
     - `name` (String): The name of the database to delete.
   - **Returns**: An `IDBOpenDBRequest` object that can be used to monitor the deletion process.

### Example
```javascript
// Creating or opening a database
const request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    // Create an object store if it doesn't exist
    if (!db.objectStoreNames.contains("myObjectStore")) {
        db.createObjectStore("myObjectStore", { keyPath: "id" });
    }
};

request.onsuccess = function(event) {
    const db = event.target.result;
    console.log("Database opened successfully:", db);
};

request.onerror = function(event) {
    console.error("Database error:", event.target.error);
};

// Deleting a database
const deleteRequest = indexedDB.deleteDatabase("myDatabase");

deleteRequest.onsuccess = function() {
    console.log("Database deleted successfully");
};

deleteRequest.onerror = function(event) {
    console.error("Database deletion failed:", event.target.error);
};
```

## Explanation
### Common Pitfalls
- **Versioning Issues**: When opening a database, if the version number is lower than the existing database version, the `onupgradeneeded` event will not fire.
- **Asynchronous Nature**: IndexedDB operations are asynchronous. Make sure to handle requests using the appropriate event handlers (`onsuccess`, `onerror`, etc.).
- **Browser Support**: While most modern browsers support IndexedDB, it is crucial to check compatibility, especially for older versions.

### Gotchas
- **Object Store Creation**: Object stores must be created during the `onupgradeneeded` event; attempting to create them afterward will fail.
- **Data Types**: IndexedDB does not support all data types. For example, functions or DOM elements cannot be stored directly.
  
### Additional Notes
- IndexedDB is more suitable for large amounts of data that need to be queried efficiently.
- Use the `indexedDB` global object to access `IDBFactory`, which provides methods to interact with the database.

## One Line Summary
`IDBFactory` is the interface providing essential methods for managing IndexedDB databases in JavaScript applications.