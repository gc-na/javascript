<!--
Meta Description: # IDBFactory：JavaScript 的 IndexedDB 工廠接口 ## 概述 IDBFactory 是一個用於創建和操作 IndexedDB 數據庫的接口，允許開發者在瀏覽器中儲存大量結構化數據。它提供了 API 來開啟數據庫連接、創建事務以及管理數據庫版本。 ## 文件說明 IDB...
Meta Keywords: event, idbfactory, indexeddb, function, javascript
-->

# IDBFactory：JavaScript 的 IndexedDB 工廠接口

## 概述
IDBFactory 是一個用於創建和操作 IndexedDB 數據庫的接口，允許開發者在瀏覽器中儲存大量結構化數據。它提供了 API 來開啟數據庫連接、創建事務以及管理數據庫版本。

## 文件說明
IDBFactory 接口是 Web Indexed Database API 的一部分，主要用於處理數據庫的創建和版本管理。透過 IDBFactory，開發者可以使用以下方法：

- `open()`: 開啟一個已存在的數據庫或創建一個新數據庫。
- `deleteDatabase()`: 刪除指定的數據庫。

這些方法使得開發者能夠靈活管理應用程序的本地數據存儲，並且能夠在用戶的瀏覽器中持久化數據，從而提升用戶體驗。

### 方法說明

#### 1. open(name, version)
- **參數**:
  - `name`: 數據庫的名稱（字串）。
  - `version`: 數據庫的版本（整數）。如果版本號高於現有數據庫，則觸發 `onupgradeneeded` 事件。

- **回傳值**: 返回一個 IDBOpenDBRequest 對象，用於處理數據庫打開的異步請求。

#### 2. deleteDatabase(name)
- **參數**:
  - `name`: 想要刪除的數據庫名稱（字串）。

- **回傳值**: 返回一個 IDBOpenDBRequest 對象，用於處理刪除數據庫的異步請求。

## 範例

### 開啟數據庫
```javascript
const request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
  const db = event.target.result;
  db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
  const db = event.target.result;
  console.log("數據庫已成功開啟:", db);
};

request.onerror = function(event) {
  console.error("數據庫開啟失敗:", event.target.error);
};
```

### 刪除數據庫
```javascript
const deleteRequest = indexedDB.deleteDatabase("myDatabase");

deleteRequest.onsuccess = function() {
  console.log("數據庫已成功刪除");
};

deleteRequest.onerror = function(event) {
  console.error("刪除數據庫失敗:", event.target.error);
};
```

## 解釋
使用 IDBFactory 時，開發者需要注意以下幾個常見問題：

- **版本管理**: 當開啟一個數據庫時，若指定的版本高於現有版本，將會觸發 `onupgradeneeded` 事件，這是用來創建或更新數據庫結構的機會。
- **異步操作**: 所有 IDBFactory 的方法都是異步的，開發者需要使用事件處理程序來獲取操作結果。
- **錯誤處理**: 必須為每個請求設置錯誤處理程序，以便能夠捕捉並處理任何潛在的錯誤。

## 一句總結
IDBFactory 是 JavaScript 中用於創建和管理 IndexedDB 數據庫的核心接口，提供了靈活的數據存儲解決方案。