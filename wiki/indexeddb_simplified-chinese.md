<!--
Meta Description: # IndexedDB：JavaScript中的高效客户端数据库 ## 摘要 IndexedDB是一个低级别的API，允许在浏览器中存储大量结构化数据，提供事务支持以及索引功能，旨在提升Web应用的性能和用户体验。 ## 文档 ### 目的 IndexedDB是Web浏览器中的一种客户端存储解决方案...
Meta Keywords: const, event, objectstore, request, function
-->

# IndexedDB：JavaScript中的高效客户端数据库

## 摘要
IndexedDB是一个低级别的API，允许在浏览器中存储大量结构化数据，提供事务支持以及索引功能，旨在提升Web应用的性能和用户体验。

## 文档
### 目的
IndexedDB是Web浏览器中的一种客户端存储解决方案，旨在存储大量数据并提供快速访问。它支持异步操作，使得应用在处理数据时不会阻塞用户界面。

### 用法
IndexedDB的基本用法包括：
1. 打开数据库：使用`indexedDB.open()`方法。
2. 创建对象存储：在数据库版本变更时，使用`onupgradeneeded`事件创建对象存储。
3. 增加、读取、更新和删除数据：通过事务管理这些操作。

### 详细说明
- **创建和打开数据库**：
  ```javascript
  const request = indexedDB.open("myDatabase", 1);
  request.onsuccess = function(event) {
      const db = event.target.result;
      console.log("数据库打开成功", db);
  };
  request.onerror = function(event) {
      console.error("数据库打开失败", event.target.error);
  };
  ```
- **创建对象存储**：
  ```javascript
  request.onupgradeneeded = function(event) {
      const db = event.target.result;
      const objectStore = db.createObjectStore("myObjectStore", { keyPath: "id" });
      console.log("对象存储创建成功", objectStore);
  };
  ```
- **增加数据**：
  ```javascript
  const transaction = db.transaction(["myObjectStore"], "readwrite");
  const objectStore = transaction.objectStore("myObjectStore");
  const request = objectStore.add({ id: 1, name: "Alice" });
  request.onsuccess = function() {
      console.log("数据添加成功");
  };
  ```

## 示例
### 基本使用示例
```javascript
// 打开数据库
const request = indexedDB.open("myDatabase", 1);

// 数据库版本升级时创建对象存储
request.onupgradeneeded = function(event) {
    const db = event.target.result;
    db.createObjectStore("users", { keyPath: "id" });
};

// 添加数据
request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction(["users"], "readwrite");
    const objectStore = transaction.objectStore("users");
    objectStore.add({ id: 1, name: "Alice" });
    objectStore.add({ id: 2, name: "Bob" });
};

// 查询数据
transaction.objectStore("users").get(1).onsuccess = function(event) {
    console.log("查询结果:", event.target.result);
};
```

## 说明
- **异步特性**：IndexedDB是异步的，导致代码的执行顺序可能与预期不符。确保在`onsuccess`或`onerror`回调中进行后续操作。
- **版本控制**：每次修改数据库结构时，必须更新数据库版本号，使用`onupgradeneeded`事件处理对象存储的创建和修改。
- **浏览器支持**：虽然现代浏览器普遍支持IndexedDB，但仍需考虑某些旧版浏览器的兼容性。

## 一句话总结
IndexedDB是JavaScript中的一个强大工具，用于在客户端有效存储和管理大量结构化数据。