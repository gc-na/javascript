<!--
Meta Description: # IDBIndex：JavaScript 中的索引DB接口 ## 概述 IDBIndex 是一個在 IndexedDB 中用來查詢資料的接口。它提供了一種高效的方式來從資料庫中檢索特定的資料，尤其是當資料集較大時。 ## 文檔 ### 目的 IDBIndex 允許開發者在 IndexedDB 中基...
Meta Keywords: idbindex, let, event, indexeddb, objectstore
-->

# IDBIndex：JavaScript 中的索引DB接口

## 概述
IDBIndex 是一個在 IndexedDB 中用來查詢資料的接口。它提供了一種高效的方式來從資料庫中檢索特定的資料，尤其是當資料集較大時。

## 文檔
### 目的
IDBIndex 允許開發者在 IndexedDB 中基於指定的鍵（key）進行查詢。這使得資料檢索更加快速和高效，特別是在有多個屬性需要索引的情況下。

### 用法
IDBIndex 的使用通常涉及以下步驟：

1. **創建資料庫**：通過 `indexedDB.open()` 方法創建或打開資料庫。
2. **創建物件存儲**：在資料庫中創建物件存儲（object store）。
3. **創建索引**：在物件存儲中創建索引以便於快速查詢。
4. **使用索引查詢**：使用 `IDBIndex` 來查詢資料。

### 詳細說明
IDBIndex 的常用方法包括：
- `get(key)`：根據指定的 key 獲取對應的資料。
- `getAll()`：獲取所有匹配的資料。
- `count()`：計算符合條件的資料數量。

### 參數
- `key`：要查詢的鍵值。
- `range`：可選，指定一個範圍來限制查詢的結果。

## 範例
### 基本使用範例
```javascript
// 創建或打開資料庫
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    let objectStore = db.createObjectStore("myStore", { keyPath: "id" });
    objectStore.createIndex("nameIndex", "name", { unique: false });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("myStore", "readonly");
    let objectStore = transaction.objectStore("myStore");
    let index = objectStore.index("nameIndex");

    // 使用索引查詢
    let indexRequest = index.get("Alice");

    indexRequest.onsuccess = function(event) {
        console.log(event.target.result);
    };
};
```

## 解釋
在使用 IDBIndex 時，開發者應注意以下事項：
- 確保索引的唯一性需求正確設置，否則可能會導致查詢錯誤。
- 使用 `getAll()` 方法時，注意可能會返回大量資料，可能影響性能。
- 當資料庫結構更改時，確保正確處理 `onupgradeneeded` 事件，避免資料遺失。

## 一句總結
IDBIndex 是 JavaScript 中一個強大的工具，用於在 IndexedDB 中高效地檢索和查詢資料。