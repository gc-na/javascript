<!--
Meta Description: # IDBVersionChangeEvent：JavaScript IndexedDB 版本变化事件 ## 概述 `IDBVersionChangeEvent` 是 JavaScript 中与 IndexedDB 相关的重要事件，主要用于处理数据库版本的变化。当数据库的版本发生变化时，浏览器会触发...
Meta Keywords: event, idbversionchangeevent, indexeddb, oldversion, let
-->

# IDBVersionChangeEvent：JavaScript IndexedDB 版本变化事件

## 概述
`IDBVersionChangeEvent` 是 JavaScript 中与 IndexedDB 相关的重要事件，主要用于处理数据库版本的变化。当数据库的版本发生变化时，浏览器会触发该事件，开发者可以通过监听此事件来进行相应的数据库升级操作。

## 文档
### 目的
`IDBVersionChangeEvent` 主要用于通知开发者 IndexedDB 数据库的版本变化情况。它在数据库打开请求时被使用，允许开发者在版本变化时执行必要的升级或清理工作。

### 用法
当数据库版本需要更新时，浏览器会触发 `IDBVersionChangeEvent` 事件。开发者可以在打开数据库的过程中，通过添加事件监听器来捕获此事件。

### 事件属性
- `oldVersion`: 事件触发前的数据库版本。
- `newVersion`: 事件触发后的数据库版本。

### 事件类型
该事件是 `Event` 的子类，支持标准的事件处理方法。

## 示例
### 基本用法
以下是一个基本的示例，展示如何使用 `IDBVersionChangeEvent` 监听数据库版本变化：

```javascript
let request = indexedDB.open("MyDatabase", 2);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    let oldVersion = event.oldVersion;
    let newVersion = event.newVersion;

    console.log(`数据库版本从 ${oldVersion} 更新到 ${newVersion}`);

    // 在这里执行数据库升级操作
    if (oldVersion < 1) {
        // 创建对象存储
        db.createObjectStore("users", { keyPath: "id" });
    } else if (oldVersion < 2) {
        // 更新数据库结构
        let objectStore = db.transaction("users").objectStore("users");
        objectStore.createIndex("email", "email", { unique: true });
    }
};

request.onsuccess = function(event) {
    console.log("数据库打开成功");
};

request.onerror = function(event) {
    console.error("数据库打开失败", event.target.error);
};
```

## 说明
使用 `IDBVersionChangeEvent` 时需要注意以下几点：
- **版本号管理**：在每次更改数据库结构时，确保增加版本号，否则 `onupgradeneeded` 事件不会被触发。
- **异步操作**：IndexedDB 的操作是异步的，因此在进行数据库版本更新时，确保在 `onupgradeneeded` 事件中完成所有需要的操作。
- **关闭连接**：在进行数据库版本更新时，确保没有其他连接打开，因为这可能导致版本更改失败。

## 一句话总结
`IDBVersionChangeEvent` 是用于处理 IndexedDB 数据库版本变化的重要事件，允许开发者在版本更新时执行必要的升级操作。