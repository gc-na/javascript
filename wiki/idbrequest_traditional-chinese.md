<!--
Meta Description: # IDBRequest：JavaScript 中的 IndexedDB 請求物件 ## 概述 `IDBRequest` 是 JavaScript 中 IndexedDB API 的一部分，主要用於處理異步操作的請求，並可用於進行資料庫操作，如讀取、寫入和刪除資料。 ## 文檔 `IDBReques...
Meta Keywords: event, idbrequest, indexeddb, error, let
-->

# IDBRequest：JavaScript 中的 IndexedDB 請求物件

## 概述
`IDBRequest` 是 JavaScript 中 IndexedDB API 的一部分，主要用於處理異步操作的請求，並可用於進行資料庫操作，如讀取、寫入和刪除資料。

## 文檔
`IDBRequest` 物件代表一個對 IndexedDB 的請求。當您執行資料庫操作時，該物件會返回一個請求，並可用於監聽操作的結果。這些結果可以是成功的資料或錯誤信息。使用 `IDBRequest` 可以更方便地處理資料庫中的資料，並能在操作完成後進行後續處理。

### 主要屬性
- `result`：請求成功時，返回的資料。
- `error`：請求失敗時，返回的錯誤信息。
- `readyState`：請求的當前狀態，可能的值包括 `pending`、`done`。

### 主要方法
- `onsuccess`：當請求成功時被調用的事件處理器。
- `onerror`：當請求失敗時被調用的事件處理器。

### 使用範例
以下是使用 `IDBRequest` 的基本範例：

```javascript
// 建立 IndexedDB 連接
let request = indexedDB.open("myDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction(["myObjectStore"], "readwrite");
    let objectStore = transaction.objectStore("myObjectStore");

    // 新增資料
    let addRequest = objectStore.add({ id: 1, name: "John Doe" });

    addRequest.onsuccess = function(event) {
        console.log("資料新增成功！", event.target.result);
    };

    addRequest.onerror = function(event) {
        console.error("資料新增失敗！", event.target.error);
    };
};

request.onerror = function(event) {
    console.error("資料庫連接失敗！", event.target.error);
};
```

## 解釋
在使用 `IDBRequest` 時，開發者應注意以下幾點：

- **異步操作**：所有的 IndexedDB 操作都是異步的，請求的結果不會立即返回，因此需要使用事件處理器來處理結果。
- **錯誤處理**：必須為每個請求設置 `onerror` 事件處理器，以便於捕獲並處理可能的錯誤。
- **狀態檢查**：使用 `readyState` 屬性可以檢查請求當前的狀態，有助於在調試過程中確保請求的正確性。

## 總結
`IDBRequest` 是 JavaScript 中一個重要的物件，用於處理 IndexedDB 的請求，能有效地管理資料庫操作的結果及錯誤。