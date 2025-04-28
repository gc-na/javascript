<!--
Meta Description: # IDBCursorWithValue: JavaScript 中的 IndexedDB 游標與值 ## 概述 `IDBCursorWithValue` 是 JavaScript 中 IndexedDB API 的一部分，用於對資料庫中的記錄進行遍歷。此游標不僅能夠存取資料庫中的資料，還能直接取得...
Meta Keywords: idbcursorwithvalue, indexeddb, let, cursor, event
-->

# IDBCursorWithValue: JavaScript 中的 IndexedDB 游標與值

## 概述
`IDBCursorWithValue` 是 JavaScript 中 IndexedDB API 的一部分，用於對資料庫中的記錄進行遍歷。此游標不僅能夠存取資料庫中的資料，還能直接取得與當前游標位置相關聯的值。

## 文檔
### 目的
`IDBCursorWithValue` 主要用於從 IndexedDB 數據庫中讀取數據。它允許開發者進行高效的數據檢索和操作，支持對資料庫的各種查詢和篩選。

### 使用方式
在使用 `IDBCursorWithValue` 前，您需要有一個開啟的 IndexedDB 連接以及一個目標對象存儲。使用 `IDBObjectStore.openCursor()` 方法時，您可以選擇傳回一個 `IDBCursorWithValue`。以下是此游標的基本使用步驟：

1. 開啟一個 IndexedDB 連接。
2. 獲取目標對象存儲。
3. 使用 `openCursor()` 方法來創建游標。
4. 使用游標遍歷資料，並能夠讀取當前記錄的值。

### 詳細說明
`IDBCursorWithValue` 提供了一個 `value` 屬性，該屬性返回當前游標所指向的記錄的值。這使得在遍歷資料庫時，開發者能夠更方便地訪問數據而無需再額外查詢。

## 範例
以下是使用 `IDBCursorWithValue` 的基本範例：

```javascript
// 開啟 IndexedDB 連接
let request = indexedDB.open("MyDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MyObjectStore", "readonly");
    let objectStore = transaction.objectStore("MyObjectStore");

    // 開啟游標
    let cursorRequest = objectStore.openCursor();

    cursorRequest.onsuccess = function(event) {
        let cursor = event.target.result;
        if (cursor) {
            console.log("Key: " + cursor.key + ", Value: ", cursor.value);
            cursor.continue(); // 繼續遍歷下一個記錄
        } else {
            console.log("已遍歷所有記錄");
        }
    };
};
```

## 解釋
使用 `IDBCursorWithValue` 時，常見的陷阱包括：

- 確保事務的正確性：在對象存儲中開啟游標時，必須在事務範圍內進行操作。
- 錯誤處理：需要監聽 `onerror` 事件，以便捕獲可能發生的錯誤。
- 游標的使用：若不小心未調用 `cursor.continue()`，將無法遍歷後續的記錄。

## 一句總結
`IDBCursorWithValue` 是一個便捷的工具，用於在 IndexedDB 中高效地遍歷和存取資料。