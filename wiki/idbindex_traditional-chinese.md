<!--
Meta Description: # IDBIndex：JavaScript 中的索引資料庫 ## 概述 IDBIndex 是一個在 IndexedDB API 中的關鍵組件，允許開發者為資料庫中的物件儲存格建立索引。透過索引，開發者可以更快速地查詢和檢索資料，提升應用程式的效能。 ## 文檔 ### 目的 IDBIndex 的主要...
Meta Keywords: const, idbindex, event, request, indexeddb
-->

# IDBIndex：JavaScript 中的索引資料庫

## 概述
IDBIndex 是一個在 IndexedDB API 中的關鍵組件，允許開發者為資料庫中的物件儲存格建立索引。透過索引，開發者可以更快速地查詢和檢索資料，提升應用程式的效能。

## 文檔
### 目的
IDBIndex 的主要目的是提供一種機制，讓開發者能夠在 IndexedDB 中對資料進行高效查詢。這對於大型資料集尤為重要，因為它能夠減少查詢時間並提高資料檢索效率。

### 使用方式
IDBIndex 是透過 IDBObjectStore.createIndex() 方法創建的。這個方法需要提供索引的名稱、索引的屬性及其他選項。創建後，IDBIndex 可以用於檢索資料。

### 詳細說明
- **屬性**：
  - `name`: 索引的名稱。
  - `keyPath`: 用於索引的屬性路徑。
  - `multiEntry`: 一個布林值，指示索引是否允許多重條目。
  - `unique`: 一個布林值，指示索引是否應該保持唯一性。

- **方法**：
  - `get(key)`: 通過鍵獲取資料。
  - `getAll(query)`: 獲取匹配查詢的所有資料。
  - `count(key)`: 計算與指定鍵匹配的資料數量。

## 示例
以下是創建和使用 IDBIndex 的基本示例：

```javascript
// 開啟資料庫
const request = indexedDB.open('myDatabase', 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const store = db.createObjectStore('myStore', {keyPath: 'id'});

    // 創建索引
    store.createIndex('nameIndex', 'name', { unique: false });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction(['myStore'], 'readonly');
    const store = transaction.objectStore('myStore');
    const index = store.index('nameIndex');

    // 使用索引查詢
    const request = index.get('John Doe');
    request.onsuccess = function(event) {
        console.log(event.target.result); // 輸出找到的資料
    };
};
```

## 解釋
- **常見陷阱**：
  - 在創建索引時，確保 `keyPath` 的格式正確，否則可能會導致錯誤。
  - 當使用 `getAll()` 方法時，若未提供查詢條件，可能會返回大量資料，對性能造成影響。

- **注意事項**：
  - 索引不會自動更新，當資料變更時，相關的索引也必須手動更新。
  - 在使用 `unique` 屬性時，確保資料不會重複以避免錯誤。

## 一句摘要
IDBIndex 是 JavaScript 中 IndexedDB 的一部分，提供高效的資料索引與查詢功能。