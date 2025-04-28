<!--
Meta Description: # IDBVersionChangeEvent 在 JavaScript 中的使用 ## 概述 IDBVersionChangeEvent 係一個用於 IndexedDB API 嘅事件，當資料庫版本變更時觸發。呢個事件可以幫助開發者處理資料庫結構變更，確保應用程序用戶端嘅數據與新版本保持一致。 #...
Meta Keywords: event, idbversionchangeevent, const, oldversion, request
-->

# IDBVersionChangeEvent 在 JavaScript 中的使用

## 概述
IDBVersionChangeEvent 係一個用於 IndexedDB API 嘅事件，當資料庫版本變更時觸發。呢個事件可以幫助開發者處理資料庫結構變更，確保應用程序用戶端嘅數據與新版本保持一致。

## 文檔
### 目的
IDBVersionChangeEvent 主要用於通知應用程序，當 IndexedDB 資料庫版本更新時，開發者可以根據需要進行結構調整或數據遷移。

### 使用方法
當你嘗試打開一個已有資料庫，並且指定一個高於當前版本的版本號，則會觸發 IDBVersionChangeEvent。這個事件提供了資料庫的舊版本號，讓開發者可以根據需要進行相應的數據處理。

### 事件屬性
- `oldVersion`: 代表事件發生前的資料庫版本號。
- `newVersion`: 代表事件發生後的資料庫版本號（如果有的話）。

### 監聽事件
要使用 IDBVersionChangeEvent，開發者需要在打開資料庫時設置事件監聽器，然後對事件進行處理。

```javascript
const request = indexedDB.open("myDatabase", 2);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const oldVersion = event.oldVersion;
    const newVersion = event.newVersion;

    console.log(`舊版本: ${oldVersion}, 新版本: ${newVersion}`);

    // 在這裡進行版本升級處理
    if (oldVersion < 1) {
        // 創建物件存儲
        db.createObjectStore("myObjectStore", { keyPath: "id" });
    } else if (oldVersion < 2) {
        // 增加索引
        const objectStore = db.transaction("myObjectStore").objectStore("myObjectStore");
        objectStore.createIndex("name", "name", { unique: false });
    }
};
```

## 例子
以下是一個簡單的示例，展示如何使用 IDBVersionChangeEvent 來處理資料庫版本的變更。

```javascript
const request = indexedDB.open("exampleDB", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    console.log("資料庫升級中...");

    // 創建一個名為 "users" 的物件存儲
    const objectStore = db.createObjectStore("users", { keyPath: "id" });
    objectStore.createIndex("name", "name", { unique: false });
};

request.onsuccess = function(event) {
    console.log("資料庫已成功開啟");
};

request.onerror = function(event) {
    console.error("資料庫開啟失敗: ", event.target.error);
};
```

## 解釋
使用 IDBVersionChangeEvent 時，開發者需要注意以下幾點：
- 資料庫版本號必須高於當前版本，否則不會觸發事件。
- 在 `onupgradeneeded` 事件中進行結構變更時，必須小心操作，以免數據丟失。
- 如果不處理 `onupgradeneeded` 事件，資料庫將無法升級，並且會導致應用程序錯誤。

## 一句總結
IDBVersionChangeEvent 係一個用於處理 IndexedDB 資料庫版本變更嘅重要事件，幫助開發者進行數據結構的調整和升級。