<!--
Meta Description: # IDBTransaction：JavaScript 中的 IndexedDB 交易 ## 簡介 `IDBTransaction` 是一個在 JavaScript 的 IndexedDB API 中使用的接口，負責管理對數據庫的事務。它允許開發者以原子方式執行一系列數據庫操作，確保在處理期間的數據...
Meta Keywords: transaction, idbtransaction, let, javascript, indexeddb
-->

# IDBTransaction：JavaScript 中的 IndexedDB 交易

## 簡介
`IDBTransaction` 是一個在 JavaScript 的 IndexedDB API 中使用的接口，負責管理對數據庫的事務。它允許開發者以原子方式執行一系列數據庫操作，確保在處理期間的數據一致性和完整性。

## 文檔
### 目的
`IDBTransaction` 的主要目的是提供一種安全的方式來執行多個數據庫操作，確保這些操作要麼全部成功，要麼全部失敗，從而避免數據不一致的情況出現。

### 使用方式
創建 `IDBTransaction` 的一般流程如下：
1. 使用 `IDBDatabase.transaction()` 方法來初始化一個新的事務。
2. 指定要訪問的對象存儲（object store）和事務的模式（如 `readwrite` 或 `readonly`）。
3. 在事務內部執行讀取或寫入操作。
4. 使用 `transaction.oncomplete`、`transaction.onerror` 和 `transaction.onabort` 事件來處理事務的結果。

### 詳細說明
- **事務模式**：
  - `readwrite`：允許讀取和寫入操作。
  - `readonly`：僅允許讀取操作。
  
- **事件處理**：
  - `oncomplete`：當事務成功完成時觸發。
  - `onerror`：當事務發生錯誤時觸發。
  - `onabort`：當事務被中止時觸發。

- **範圍**：`IDBTransaction` 只能在創建它的數據庫連接上下文中使用，並且在事務完成後無法再訪問。

## 範例
以下是如何使用 `IDBTransaction` 的基本範例：

```javascript
// 打開數據庫
let request = indexedDB.open("myDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;

    // 開始一個事務
    let transaction = db.transaction(["myObjectStore"], "readwrite");

    // 獲取對象存儲
    let objectStore = transaction.objectStore("myObjectStore");

    // 添加數據
    let addRequest = objectStore.add({ id: 1, name: "Item 1" });

    addRequest.onsuccess = function() {
        console.log("數據已成功添加");
    };

    // 處理事務完成事件
    transaction.oncomplete = function() {
        console.log("事務已完成");
    };

    // 處理事務錯誤事件
    transaction.onerror = function() {
        console.log("事務出錯：", transaction.error);
    };
};
```

## 解釋
- **常見陷阱**：
  - 忘記檢查事務的狀態，可能導致在事務完成後嘗試執行操作。
  - 在事務範圍外使用 `IDBTransaction` 的方法，將導致錯誤。
  
- **額外注意**：
  - 事務的存活時間取決於事務內部的操作。如果事務內部有異步操作，請確保這些操作在事務完成之前完成。
  - 當事務被中止時，對象存儲中的所有未提交的變更都將被撤銷。

## 簡短總結
`IDBTransaction` 提供了一種安全的方式來在 JavaScript 中管理 IndexedDB 的數據庫事務，確保數據操作的原子性和一致性。