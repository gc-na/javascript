<!--
Meta Description: # IDBTransaction: JavaScript 中的 IndexedDB 交易管理 ## 概述 `IDBTransaction` 是一個用於處理 IndexedDB 的交易的介面，允許開發者在資料庫中執行一系列操作，以確保數據的一致性和完整性。 ## 文檔 `IDBTransaction`...
Meta Keywords: indexeddb, idbtransaction, let, transaction, function
-->

# IDBTransaction: JavaScript 中的 IndexedDB 交易管理

## 概述
`IDBTransaction` 是一個用於處理 IndexedDB 的交易的介面，允許開發者在資料庫中執行一系列操作，以確保數據的一致性和完整性。

## 文檔
`IDBTransaction` 是在 IndexedDB API 中使用的一個核心組件，主要負責管理資料庫的讀取和寫入操作。當你在 IndexedDB 中執行操作時，這些操作是被包裝在交易中的。每個交易都可以是讀取型或寫入型，並且可以包含多個資料庫請求。

### 目的
- 確保資料庫操作的原子性：要麼所有操作成功，要麼都不執行。
- 提供錯誤處理機制，讓開發者能夠透過事件監聽器捕獲交易的成功或失敗。

### 用法
創建一個 `IDBTransaction` 實例時，你需要一個資料庫連接和一組指定的物件存儲區（Object Store）來進行操作。以下是創建交易的一般步驟：

1. 打開一個資料庫連接。
2. 使用 `transaction` 方法創建交易。
3. 在交易中執行所需的操作。

## 示例
### 基本用法範例
```javascript
// 打開資料庫
let request = indexedDB.open("MyDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;

    // 創建交易
    let transaction = db.transaction(["MyObjectStore"], "readwrite");

    // 獲取物件存儲區
    let objectStore = transaction.objectStore("MyObjectStore");

    // 添加數據
    let addRequest = objectStore.add({ id: 1, name: "Test" });

    addRequest.onsuccess = function() {
        console.log("數據添加成功");
    };

    addRequest.onerror = function() {
        console.error("數據添加失敗");
    };
};

// 錯誤處理
request.onerror = function(event) {
    console.error("資料庫打開失敗:", event.target.errorCode);
};
```

## 解釋
### 常見問題
- **交易的範圍**：一個交易只能針對指定的物件存儲區進行操作。如果嘗試訪問其他物件存儲區，將會導致錯誤。
- **交易的生命週期**：交易會在所有請求完成後自動結束。如果請求失敗，則整個交易會回滾。
- **事件處理**：必須為交易的成功和失敗分別設置事件監聽器，以便能夠正確處理結果。

### 注意事項
- 在進行寫入操作時，請確保資料庫沒有被其他交易鎖定，否則會導致寫入失敗。
- 在使用 `IDBTransaction` 時，建議熟悉 IndexedDB 的工作原理，以便能夠更好地處理異步操作和錯誤。

## 一句總結
`IDBTransaction` 是一個關鍵的 IndexedDB 介面，負責管理資料庫的交易，以確保數據的一致性和完整性。