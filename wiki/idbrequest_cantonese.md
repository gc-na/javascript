<!--
Meta Description: # IDBRequest：JavaScript 中的 IndexedDB 請求物件 ## 概述 IDBRequest 是 JavaScript 中用於處理 IndexedDB 請求的物件。它允許開發者發送請求以讀取或寫入資料庫，並通過事件來監控請求的狀態。 ## 文檔 ### 目的 IDBReque...
Meta Keywords: event, idbrequest, indexeddb, error, let
-->

# IDBRequest：JavaScript 中的 IndexedDB 請求物件

## 概述
IDBRequest 是 JavaScript 中用於處理 IndexedDB 請求的物件。它允許開發者發送請求以讀取或寫入資料庫，並通過事件來監控請求的狀態。

## 文檔
### 目的
IDBRequest 物件的主要目的是提供一個接口，使開發者能夠與 IndexedDB 進行互動。這些請求可用於創建、讀取、更新和刪除數據（CRUD 操作）。

### 使用方法
當開發者調用 IndexedDB 的方法（如 `add()`, `put()`, `get()` 等）時，將返回一個 IDBRequest 物件。這個物件包含了請求的狀態和結果，可以通過事件監聽器來獲取結果或錯誤信息。

#### 屬性
- `result`: 請求成功完成後的結果。
- `error`: 請求失敗時的錯誤信息。
- `readyState`: 請求的當前狀態，可能的值有 `pending`、`done`。

#### 事件
- `onsuccess`: 當請求成功時觸發。
- `onerror`: 當請求失敗時觸發。

### 例子
以下是一個簡單的使用例子：

```javascript
let request = indexedDB.open("MyDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MyObjectStore", "readwrite");
    let objectStore = transaction.objectStore("MyObjectStore");
    let addRequest = objectStore.add({ id: 1, name: "Sample" });

    addRequest.onsuccess = function(event) {
        console.log("資料已成功新增:", event.target.result);
    };

    addRequest.onerror = function(event) {
        console.error("新增資料時發生錯誤:", event.target.error);
    };
};

request.onerror = function(event) {
    console.error("開啟資料庫時發生錯誤:", event.target.error);
};
```

## 解釋
當使用 IDBRequest 時，開發者需要注意以下幾點：
- 確保在操作資料庫之前，資料庫已經成功開啟。
- 監聽 `onsuccess` 和 `onerror` 事件，以便處理請求的結果和錯誤。
- 當請求尚未完成時，不要嘗試訪問 `result` 或 `error` 屬性，因為這可能會導致錯誤。

## 一句總結
IDBRequest 是 JavaScript 中用於與 IndexedDB 進行資料請求的關鍵物件，提供了簡單的 API 來處理 CRUD 操作。