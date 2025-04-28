<!--
Meta Description: # IDBCursorWithValue：JavaScript 中的 IndexedDB 遍歷器 ## 概述 IDBCursorWithValue 是一個在 JavaScript 中用於 IndexedDB 的接口，提供了一種在資料庫中遍歷記錄的方式，並且能夠直接訪問與每個游標相關聯的值。 ## 文...
Meta Keywords: idbcursorwithvalue, indexeddb, let, cursor, javascript
-->

# IDBCursorWithValue：JavaScript 中的 IndexedDB 遍歷器

## 概述
IDBCursorWithValue 是一個在 JavaScript 中用於 IndexedDB 的接口，提供了一種在資料庫中遍歷記錄的方式，並且能夠直接訪問與每個游標相關聯的值。

## 文檔
### 目的
IDBCursorWithValue 的主要目的是允許開發者在 IndexedDB 資料庫中遍歷資料，並同時獲取每個記錄的鍵和值。這對於需要逐一處理資料的應用場景特別有用。

### 使用方法
要使用 IDBCursorWithValue，首先需要建立一個 IndexedDB 連接，然後使用 `IDBObjectStore.openCursor()` 方法來創建一個游標。這個游標可以被用來訪問資料庫中的記錄。當使用 `openCursor()` 方法時，傳遞 `IDBCursorWithValue` 參數可以獲取與鍵相關聯的值。

### 詳細信息
- **屬性**：
  - `value`：返回當前游標指向的記錄的值。
  - `key`：返回當前游標指向的記錄的鍵。

- **方法**：
  - `continue(key)`：將游標移動到下個匹配的記錄。
  - `delete()`：刪除當前游標指向的記錄。

這些屬性和方法使得 IDBCursorWithValue 成為操作 IndexedDB 中資料的強大工具。

## 範例
以下是使用 IDBCursorWithValue 的基本範例：

```javascript
// 打開 IndexedDB 資料庫
let request = indexedDB.open("myDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction(["myStore"], "readonly");
    let objectStore = transaction.objectStore("myStore");
    
    // 開啟游標
    let cursorRequest = objectStore.openCursor();

    cursorRequest.onsuccess = function(event) {
        let cursor = event.target.result;
        if (cursor) {
            console.log("鍵: " + cursor.key + ", 值: ", cursor.value);
            cursor.continue(); // 繼續到下一個記錄
        } else {
            console.log("已經到達最後一個記錄");
        }
    };
};
```

## 解釋
使用 IDBCursorWithValue 時，開發者需注意以下幾點：
- 確保資料庫已經成功打開，否則會導致游標操作失敗。
- 當使用 `continue()` 方法時，游標會自動移動到下一個記錄，因此需確保有正確的邏輯來處理資料。
- 如果資料庫中沒有更多記錄，游標的 `result` 將是 `null`，開發者需處理這種情況以避免錯誤。

## 一句總結
IDBCursorWithValue 是 JavaScript 中用於遍歷 IndexedDB 記錄並同時獲取鍵和值的強大工具。