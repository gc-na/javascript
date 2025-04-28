<!--
Meta Description: # IDBDatabase：JavaScript 中的 IndexedDB 資料庫介面 ## 簡介 IDBDatabase 是 JavaScript 中 IndexedDB API 的一部分，用於在客戶端儲存大量結構化資料。這個介面允許開發者建立、讀取和更新資料庫，並提供事務的支持。 ## 文件說明...
Meta Keywords: idbdatabase, indexeddb, const, event, store
-->

# IDBDatabase：JavaScript 中的 IndexedDB 資料庫介面

## 簡介
IDBDatabase 是 JavaScript 中 IndexedDB API 的一部分，用於在客戶端儲存大量結構化資料。這個介面允許開發者建立、讀取和更新資料庫，並提供事務的支持。

## 文件說明
IDBDatabase 介面代表一個資料庫實例，提供多種方法以操作資料庫中的資料。使用 IndexedDB，開發者可以在用戶的瀏覽器中儲存資料，這對於需要離線功能的 web 應用程式特別重要。

### 目的
IDBDatabase 主要目的是讓開發者能夠在客戶端儲存和檢索結構化資料，並在不需重新加載頁面的情況下進行資料操作。

### 使用方法
要使用 IDBDatabase，首先需要建立一個資料庫連接。這通常透過 `indexedDB.open()` 方法進行。當資料庫成功打開後，將會觸發 `upgradeneeded` 事件，開發者可以在該事件中創建物件存儲 (Object Store) 和索引 (Index)。

#### 主要方法
- `transaction(storeNames, mode)`：啟動一個事務。
- `close()`：關閉資料庫連接。
- `deleteObjectStore(name)`：刪除指定的物件存儲。
- `version`：獲取資料庫版本。

### 資料庫的版本管理
IDBDatabase 支援版本控制，透過 `version` 屬性，開發者可以管理資料庫的結構變更。當資料庫版本號增加時，將會觸發 `upgradeneeded` 事件。

## 範例
以下是使用 IDBDatabase 進行基本操作的範例：

```javascript
// 開啟或建立資料庫
const request = indexedDB.open('MyDatabase', 1);

request.onupgradeneeded = function(event) {
  const db = event.target.result;
  // 建立物件存儲
  const objectStore = db.createObjectStore('MyStore', { keyPath: 'id' });
};

request.onsuccess = function(event) {
  const db = event.target.result;
  // 開始一個事務
  const transaction = db.transaction('MyStore', 'readwrite');
  const store = transaction.objectStore('MyStore');

  // 新增資料
  store.add({ id: 1, name: 'Alice' });
  store.add({ id: 2, name: 'Bob' });

  // 讀取資料
  const getRequest = store.get(1);
  getRequest.onsuccess = function(event) {
    console.log(event.target.result); // { id: 1, name: 'Alice' }
  };
};
```

## 解釋
在使用 IDBDatabase 時，開發者需要注意以下幾點：
- **異步操作**：IndexedDB 的操作是非同步的，因此需要使用事件處理程序來處理成功或失敗的情況。
- **版本升級**：當資料庫版本升級時，必須在 `upgradeneeded` 事件中進行結構調整，否則可能會導致資料遺失。
- **事務範圍**：事務是在特定的物件存儲中進行的，開發者需確保在事務完成之前不關閉資料庫。

## 一句總結
IDBDatabase 是 JavaScript 中用於操作 IndexedDB 的介面，提供強大的客戶端資料儲存能力。