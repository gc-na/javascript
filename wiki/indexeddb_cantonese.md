<!--
Meta Description: # 使用 JavaScript 操作 IndexedDB 的 完整指南 ## 簡介 IndexedDB 是一種在用戶瀏覽器中儲存大量結構化數據的技術，讓開發者能夠在客戶端進行高效的查詢和更新。它適合用於儲存需要離線訪問或快速檢索的數據。 ## 文檔 ### 目的 IndexedDB 允許網站和應用程...
Meta Keywords: indexeddb, let, event, function, objectstore
-->

# 使用 JavaScript 操作 IndexedDB 的 完整指南

## 簡介
IndexedDB 是一種在用戶瀏覽器中儲存大量結構化數據的技術，讓開發者能夠在客戶端進行高效的查詢和更新。它適合用於儲存需要離線訪問或快速檢索的數據。

## 文檔
### 目的
IndexedDB 允許網站和應用程序在用戶的瀏覽器中儲存數據，從而提供離線功能和加快數據存取速度。這對於需要大量數據處理的 Web 應用程序尤為重要。

### 使用方法
1. **打開數據庫**：使用 `indexedDB.open()` 方法來創建或打開數據庫。
2. **創建對象存儲區**：在數據庫的升級事件中使用 `createObjectStore()` 方法來創建對象存儲區。
3. **添加數據**：使用 `add()`, `put()`, 或 `delete()` 方法來管理數據。
4. **檢索數據**：通過 `get()` 方法獲取數據，或使用 `openCursor()` 進行遍歷。
5. **關閉數據庫**：操作完成後，使用 `close()` 方法來關閉數據庫連接。

### 詳細說明
IndexedDB 提供了事務支持，可以在一個事務內進行多個數據操作。每個數據庫都有版本號，當版本號變更時，會觸發升級事件，讓開發者能夠進行必要的數據結構變更。IndexedDB 的 API 主要是基於異步操作，這樣可以避免阻塞主執行緒。

## 示例
以下是一個簡單的 IndexedDB 使用示例：

```javascript
// 打開數據庫
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    // 創建對象存儲區
    let objectStore = db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    
    // 添加數據
    let transaction = db.transaction("myObjectStore", "readwrite");
    let objectStore = transaction.objectStore("myObjectStore");
    let data = { id: 1, name: "John Doe" };
    
    let addRequest = objectStore.add(data);
    
    addRequest.onsuccess = function() {
        console.log("數據添加成功");
    };
    
    // 檢索數據
    let getRequest = objectStore.get(1);
    getRequest.onsuccess = function() {
        console.log("獲取到的數據:", getRequest.result);
    };
};

request.onerror = function(event) {
    console.error("數據庫開啟失敗:", event.target.error);
};
```

## 解釋
- **常見陷阱**：在 IndexedDB 中，所有操作都是異步的，這意味著你需要妥善處理回調函數，否則可能會導致數據未正確加載。
- **版本管理**：每當你需要更改數據庫結構時，你必須增加版本號，否則將不會觸發升級事件。
- **數據存儲限制**：雖然 IndexedDB 可以儲存大量數據，但不同瀏覽器對儲存容量有不同的限制。

## 總結
IndexedDB 是一種強大的客戶端數據存儲解決方案，適合需要高效數據處理和離線功能的 Web 應用程序。