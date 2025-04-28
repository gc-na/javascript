<!--
Meta Description: # IDBFactory: JavaScript 的 IndexedDB 工廠接口 ## 概述 IDBFactory 是一個與 IndexedDB 相關的接口，它提供了用於創建和打開資料庫的功能。IndexedDB 是一種用於在客戶端存儲大量資料的低階 API，適合用於離線應用程式。 ## 文件說明...
Meta Keywords: indexeddb, event, idbfactory, const, javascript
-->

# IDBFactory: JavaScript 的 IndexedDB 工廠接口

## 概述
IDBFactory 是一個與 IndexedDB 相關的接口，它提供了用於創建和打開資料庫的功能。IndexedDB 是一種用於在客戶端存儲大量資料的低階 API，適合用於離線應用程式。

## 文件說明
IDBFactory 的主要目的是為了管理和操作 IndexedDB 資料庫。這個接口有助於開發者創建新的資料庫、打開已存在的資料庫以及刪除資料庫。IDBFactory 通常不直接被使用，而是透過 window.indexedDB 屬性來訪問。

### 使用方法
IDBFactory 提供了以下幾種方法：

1. **open()**: 用於打開一個資料庫。如果資料庫不存在，則會創建一個新資料庫。
   ```javascript
   const request = indexedDB.open("myDatabase", 1);
   ```

2. **deleteDatabase()**: 用於刪除指定的資料庫。
   ```javascript
   const deleteRequest = indexedDB.deleteDatabase("myDatabase");
   ```

### 參數
- `open(name, version)`:
  - `name`: 資料庫的名稱（字串）。
  - `version`: 資料庫的版本（整數）。

- `deleteDatabase(name)`:
  - `name`: 要刪除的資料庫名稱（字串）。

## 範例
以下是使用 IDBFactory 的基本範例：

### 打開資料庫
```javascript
const request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    db.createObjectStore("myStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    console.log("資料庫已成功打開:", db);
};

request.onerror = function(event) {
    console.error("打開資料庫時發生錯誤:", event.target.error);
};
```

### 刪除資料庫
```javascript
const deleteRequest = indexedDB.deleteDatabase("myDatabase");

deleteRequest.onsuccess = function(event) {
    console.log("資料庫已成功刪除");
};

deleteRequest.onerror = function(event) {
    console.error("刪除資料庫時發生錯誤:", event.target.error);
};
```

## 解釋
在使用 IDBFactory 時，開發者需要注意以下幾點：

- **版本控制**: 當開啟一個資料庫時，應該小心版本管理。如果版本號較高，onupgradeneeded 事件將會被觸發，這是資料庫結構升級的好時機。
- **異步性**: 所有對資料庫的操作都是異步的，因此需要使用回調函數來處理成功和錯誤的情況。
- **瀏覽器支持**: 雖然大部分現代瀏覽器都支持 IndexedDB，但在某些舊版本的瀏覽器中可能不支援，因此在開發時需進行測試。

## 總結
IDBFactory 是一個關鍵的接口，用來管理 IndexedDB 資料庫，提供了開啟和刪除資料庫的功能。