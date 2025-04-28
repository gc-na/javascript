<!--
Meta Description: # IDBObjectStore：JavaScript 的 IndexedDB 物件存儲 ## 概述 `IDBObjectStore` 是 JavaScript 中 IndexedDB API 的一部分，允許開發者在用戶的瀏覽器中以非關聯型的方式儲存和檢索資料。它提供了一個簡單的接口來操作資料集合，...
Meta Keywords: const, event, objectstore, idbobjectstore, javascript
-->

# IDBObjectStore：JavaScript 的 IndexedDB 物件存儲

## 概述
`IDBObjectStore` 是 JavaScript 中 IndexedDB API 的一部分，允許開發者在用戶的瀏覽器中以非關聯型的方式儲存和檢索資料。它提供了一個簡單的接口來操作資料集合，支持事務性操作。

## 文檔
### 目的
`IDBObjectStore` 的主要目的是提供一個可持久化存儲資料的結構，適用於需要存儲大量資料的 Web 應用程序。它支持對象的儲存、讀取、更新和刪除，並且允許使用事務來確保資料一致性。

### 使用方法
使用 `IDBObjectStore` 前，需要先創建一個 IndexedDB 數據庫並建立一個物件存儲。以下是基本的步驟：

1. **打開數據庫**：
   ```javascript
   const request = indexedDB.open('myDatabase', 1);
   request.onupgradeneeded = function(event) {
       const db = event.target.result;
       db.createObjectStore('myObjectStore', { keyPath: 'id' });
   };
   ```

2. **獲取物件存儲**：
   ```javascript
   const db = request.result;
   const transaction = db.transaction('myObjectStore', 'readwrite');
   const objectStore = transaction.objectStore('myObjectStore');
   ```

3. **添加資料**：
   ```javascript
   const data = { id: 1, name: 'Alice' };
   objectStore.add(data);
   ```

4. **讀取資料**：
   ```javascript
   const getRequest = objectStore.get(1);
   getRequest.onsuccess = function(event) {
       console.log(event.target.result);
   };
   ```

### 詳細說明
- **事務**：`IDBObjectStore` 操作在事務內執行，確保資料的完整性。
- **鍵值**：每個物件存儲使用一個唯一的 `keyPath` 作為鍵，這可以是物件的某個屬性。
- **方法**：包括 `add()`, `put()`, `delete()`, `get()`, `getAll()` 等，這些方法允許對資料進行不同的操作。

## 示例
### 基本使用範例
以下是一個創建、添加和讀取資料的簡單範例：

```javascript
const request = indexedDB.open('myDatabase', 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    db.createObjectStore('myObjectStore', { keyPath: 'id' });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction('myObjectStore', 'readwrite');
    const objectStore = transaction.objectStore('myObjectStore');

    // 添加資料
    objectStore.add({ id: 1, name: 'Alice' });

    // 讀取資料
    const getRequest = objectStore.get(1);
    getRequest.onsuccess = function(event) {
        console.log(event.target.result); // { id: 1, name: 'Alice' }
    };
};
```

## 解釋
- **常見陷阱**：確保在使用 `IDBObjectStore` 前數據庫已成功打開，否則將無法進行任何操作。
- **錯誤處理**：記得為所有請求添加錯誤處理，以便能夠捕捉並處理任何異常情況。
- **性能考量**：大量資料的操作可能會影響性能，建議對批量操作進行優化。

## 總結
`IDBObjectStore` 提供了一個靈活的接口，用於在瀏覽器中以非關聯型方式儲存和管理資料。