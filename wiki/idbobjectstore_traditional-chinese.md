<!--
Meta Description: # IDBObjectStore：JavaScript 中的 IndexedDB 物件存儲 ## 簡介 IDBObjectStore 是 JavaScript 中 IndexedDB API 的一部分，提供了一個用於儲存和檢索資料的結構化存儲解決方案。透過 IDBObjectStore，開發者可以在...
Meta Keywords: const, javascript, idbobjectstore, event, request
-->

# IDBObjectStore：JavaScript 中的 IndexedDB 物件存儲

## 簡介
IDBObjectStore 是 JavaScript 中 IndexedDB API 的一部分，提供了一個用於儲存和檢索資料的結構化存儲解決方案。透過 IDBObjectStore，開發者可以在用戶的瀏覽器中以非關聯式的方式儲存大量資料。

## 文件說明
IDBObjectStore 的主要目的是提供一個介面來儲存 JavaScript 對象，這些對象可以是基本類型或其他複雜類型的資料。每個 IDBObjectStore 都與一個特定的資料庫版本相關聯，並且可以在事務中進行讀取和寫入操作。

### 主要功能
- **資料儲存**：允許儲存 JavaScript 對象，包括陣列和物件。
- **事務管理**：在事務中安全地進行讀取和寫入操作。
- **鍵值存取**：支持使用鍵來快速存取資料。
- **索引**：可以創建索引以提高查詢性能。

### 使用方式
在使用 IDBObjectStore 時，首先需要創建一個 IndexedDB 資料庫，然後可以在該資料庫中創建一個物件存儲。以下是基本步驟：

1. 打開資料庫：
   ```javascript
   const request = indexedDB.open('myDatabase', 1);
   ```

2. 創建物件存儲：
   ```javascript
   request.onupgradeneeded = function(event) {
       const db = event.target.result;
       db.createObjectStore('myObjectStore', { keyPath: 'id' });
   };
   ```

3. 寫入資料：
   ```javascript
   const transaction = db.transaction(['myObjectStore'], 'readwrite');
   const objectStore = transaction.objectStore('myObjectStore');
   const data = { id: 1, name: 'John Doe' };
   objectStore.add(data);
   ```

4. 讀取資料：
   ```javascript
   const request = objectStore.get(1);
   request.onsuccess = function(event) {
       console.log(event.target.result);
   };
   ```

## 範例
### 寫入和讀取資料的基本範例
```javascript
const request = indexedDB.open('testDB', 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    db.createObjectStore('users', { keyPath: 'id' });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction(['users'], 'readwrite');
    const store = transaction.objectStore('users');

    store.add({ id: 1, name: 'Alice' });
    
    const getRequest = store.get(1);
    getRequest.onsuccess = function() {
        console.log(getRequest.result); // { id: 1, name: 'Alice' }
    };
};
```

## 解釋
使用 IDBObjectStore 時，有些常見的陷阱需要注意：
- **版本控制**：每次更改資料庫結構時，必須更新版本號以觸發 `onupgradeneeded` 事件。
- **事務範圍**：所有的讀寫操作必須在事務內進行，否則將會失敗。
- **非同步性**：IndexedDB 操作是非同步的，因此需要使用事件或回調來處理結果。

## 一句總結
IDBObjectStore 是一個強大的 JavaScript API，允許開發者在瀏覽器中以結構化的方式儲存和管理大量資料。