<!--
Meta Description: # IDBDatabase：JavaScript 中的 IndexedDB 數據庫對象 ## 概述 IDBDatabase 是一個接口，提供對 IndexedDB 數據庫的訪問，允許開發者儲存和檢索大量結構化數據。此接口是 Web API 的一部分，專為在客戶端存儲數據而設計。 ## 文檔 ### ...
Meta Keywords: idbdatabase, indexeddb, let, event, transaction
-->

# IDBDatabase：JavaScript 中的 IndexedDB 數據庫對象

## 概述
IDBDatabase 是一個接口，提供對 IndexedDB 數據庫的訪問，允許開發者儲存和檢索大量結構化數據。此接口是 Web API 的一部分，專為在客戶端存儲數據而設計。

## 文檔
### 目的
IDBDatabase 主要用於與 IndexedDB 數據庫進行交互，支持創建、讀取、更新和刪除（CRUD）操作。它可以儲存大量的數據，並且可以在網頁刷新或關閉後持久化。

### 使用方法
要使用 IDBDatabase，首先需要創建一個 IndexedDB 數據庫並獲取其實例。這通常通過 `indexedDB.open()` 方法來實現。然後，可以通過該實例執行各種操作。

以下是 IDBDatabase 的一些重要屬性和方法：
- `transaction()`: 創建一個新的事務。
- `objectStoreNames`: 返回數據庫中所有物件存儲的名稱。
- `close()`: 關閉數據庫連接。

### 詳細信息
IDBDatabase 會在數據庫創建或更新時觸發 `upgradeneeded` 事件。開發者可以在事件處理器內創建物件存儲和索引。IDBDatabase 的一個重要特性是它支持事務（transaction），允許對數據的原子操作。

## 示例
以下是使用 IDBDatabase 的基本範例：

```javascript
// 開啟或創建數據庫
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    // 創建一個物件存儲
    db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;

    // 創建一個事務
    let transaction = db.transaction("myObjectStore", "readwrite");
    let objectStore = transaction.objectStore("myObjectStore");

    // 添加數據
    let addRequest = objectStore.add({ id: 1, name: "John Doe" });

    addRequest.onsuccess = function() {
        console.log("數據已成功添加");
    };
};

request.onerror = function(event) {
    console.error("數據庫錯誤:", event.target.error);
};
```

## 解釋
使用 IDBDatabase 時，開發者應注意以下幾點：
- 當數據庫版本更新時，必須正確處理 `upgradeneeded` 事件。
- 確保在事務完成之前，不要關閉數據庫連接。
- 當操作較大數據集時，可能會導致性能問題，應考慮使用游標（cursor）來分批處理數據。

## 一句總結
IDBDatabase 是 JavaScript 中用於操作 IndexedDB 數據庫的接口，支持高效的客戶端數據存儲。