<!--
Meta Description: # IndexedDB：JavaScript 的高效本地數據庫 ## 概要 IndexedDB 是一種在網頁應用程序中使用的低層次的客戶端存儲解決方案，允許開發者在用戶的瀏覽器中存儲大量結構化數據。這項技術使得 Web 應用能夠在離線狀態下持久化數據，並提供高效的數據檢索能力。 ## 文件說明 ##...
Meta Keywords: indexeddb, const, objectstore, event, name
-->

# IndexedDB：JavaScript 的高效本地數據庫

## 概要
IndexedDB 是一種在網頁應用程序中使用的低層次的客戶端存儲解決方案，允許開發者在用戶的瀏覽器中存儲大量結構化數據。這項技術使得 Web 應用能夠在離線狀態下持久化數據，並提供高效的數據檢索能力。

## 文件說明
### 目的
IndexedDB 的主要目的是提供一種能夠儲存大量數據的方式，並支持複雜的查詢和事務處理。它是一個面向對象的數據庫，允許開發者創建數據庫、數據表、索引以及進行 CRUD（創建、讀取、更新、刪除）操作。

### 使用方法
在使用 IndexedDB 之前，開發者需要先打開或創建一個數據庫。這通常是通過 `indexedDB.open()` 方法來完成的。以下是基本的使用流程：

1. 打開數據庫
2. 創建對象存儲空間
3. 插入數據
4. 查詢數據
5. 更新或刪除數據

### 詳細資訊
- **數據庫版本管理**：IndexedDB 使用版本號來管理數據庫的結構變化，開發者需要處理版本升級的事件。
- **事務管理**：所有對數據庫的操作都必須在事務中進行，以確保數據的一致性。
- **異步操作**：IndexedDB 的大多數 API 是異步的，這意味著操作不會阻塞主線程。

## 示例
### 基本用法示例
```javascript
// 打開數據庫
const request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const objectStore = db.createObjectStore("myObjectStore", { keyPath: "id" });
    objectStore.createIndex("name", "name", { unique: false });
};

request.onsuccess = function(event) {
    const db = event.target.result;

    // 插入數據
    const transaction = db.transaction("myObjectStore", "readwrite");
    const objectStore = transaction.objectStore("myObjectStore");
    objectStore.add({ id: 1, name: "Alice" });

    // 查詢數據
    const getRequest = objectStore.get(1);
    getRequest.onsuccess = function(event) {
        console.log(getRequest.result); // 輸出: { id: 1, name: "Alice" }
    };
};
```

## 解釋
### 常見陷阱
- **版本控制**：如果未正確處理 `onupgradeneeded` 事件，可能會導致數據庫結構錯誤或數據丟失。
- **異步行為**：由於 IndexedDB 的操作是異步的，開發者需要謹慎處理回調函數，否則可能會出現未定義行為。
- **瀏覽器支持**：雖然大多數現代瀏覽器都支持 IndexedDB，但某些舊版瀏覽器可能不支持，開發者應該針對不同瀏覽器進行測試。

## 一句總結
IndexedDB 是一種強大的客戶端數據存儲解決方案，適合於需要高效數據處理的 Web 應用。