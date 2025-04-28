<!--
Meta Description: # IDBDatabase：JavaScript 中的 IndexedDB 数据库接口 ## 概述 `IDBDatabase` 是 JavaScript IndexedDB API 中的一个重要接口，允许开发者创建和管理客户端的数据库。它提供了对数据库的基本操作，包括事务管理、对象存储和数据检索等功...
Meta Keywords: idbdatabase, indexeddb, event, transaction, let
-->

# IDBDatabase：JavaScript 中的 IndexedDB 数据库接口

## 概述
`IDBDatabase` 是 JavaScript IndexedDB API 中的一个重要接口，允许开发者创建和管理客户端的数据库。它提供了对数据库的基本操作，包括事务管理、对象存储和数据检索等功能。

## 文档
`IDBDatabase` 接口表示一个数据库，可以通过 `indexedDB.open()` 方法打开。每个数据库包括多个对象存储，它们用于存储数据。开发者可以使用事务在对象存储中进行读写操作。

### 主要用途
- 创建和管理对象存储
- 执行事务以确保数据一致性
- 进行数据的增、删、改、查操作

### 使用方法
以下是使用 `IDBDatabase` 的基本步骤：
1. 使用 `indexedDB.open()` 方法打开或创建数据库。
2. 在 `onupgradeneeded` 事件中定义数据库的结构。
3. 使用 `transaction` 方法进行数据操作。

### 详细属性和方法
- **transaction(storeNames, mode)**：创建一个事务，用于指定的对象存储。
- **objectStore(name)**：获取指定的对象存储。
- **close()**：关闭数据库连接。
- **onversionchange**：当数据库版本发生改变时触发。

## 示例
### 创建和使用数据库
```javascript
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("myObjectStore", "readwrite");
    let store = transaction.objectStore("myObjectStore");
    
    store.add({ id: 1, name: "Alice" });
    store.add({ id: 2, name: "Bob" });
};

request.onerror = function(event) {
    console.error("Database error: " + event.target.errorCode);
};
```

## 说明
在使用 `IDBDatabase` 时，开发者需要注意以下几点：
- **版本管理**：在数据库结构变化时，必须正确处理 `onupgradeneeded` 事件。
- **异步操作**：所有操作都是异步的，需通过回调函数处理结果。
- **错误处理**：务必实现错误处理逻辑，以捕获可能发生的错误，比如数据库打开失败或事务失败。

## 一句话总结
`IDBDatabase` 是一个用于管理 IndexedDB 数据库的 JavaScript 接口，支持事务和对象存储操作，适用于客户端数据存储需求。