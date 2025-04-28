<!--
Meta Description: # IDBVersionChangeEvent：JavaScript 中的索引資料庫版本變更事件 ## 概述 `IDBVersionChangeEvent` 是一種用於處理 IndexedDB 版本變更的事件。當 IndexedDB 數據庫的版本發生變化時，此事件將被觸發，允許開發人員在版本變更時進...
Meta Keywords: event, request, const, oldversion, function
-->

# IDBVersionChangeEvent：JavaScript 中的索引資料庫版本變更事件

## 概述
`IDBVersionChangeEvent` 是一種用於處理 IndexedDB 版本變更的事件。當 IndexedDB 數據庫的版本發生變化時，此事件將被觸發，允許開發人員在版本變更時進行必要的更新或遷移操作。

## 文檔
### 目的
`IDBVersionChangeEvent` 主要用於監控數據庫版本的變更，通常在開啟數據庫時指定的版本號與數據庫中現有的版本不匹配時觸發。這對於在數據庫結構或數據模型發生變更時，執行升級或清理操作至關重要。

### 使用方式
要監聽 `IDBVersionChangeEvent`，您需要在打開數據庫時設置一個事件處理器。當版本變更事件被觸發時，您可以在事件處理器中定義所需的操作。

#### 基本語法
```javascript
const request = indexedDB.open('myDatabase', newVersion);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    // 進行版本變更的操作
};

request.onsuccess = function(event) {
    const db = event.target.result;
    // 數據庫打開成功的操作
};

request.onerror = function(event) {
    console.error('數據庫打開失敗', event);
};
```

### 事件屬性
- `oldVersion`: 數據庫的舊版本號。
- `newVersion`: 數據庫的新增版本號。

## 範例
### 示例 1：版本變更的基本處理
```javascript
const request = indexedDB.open('testDB', 2);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const oldVersion = event.oldVersion;
    const newVersion = event.newVersion;

    console.log(`版本由 ${oldVersion} 變更至 ${newVersion}`);
    
    // 創建或更新數據庫結構
    if (oldVersion < 1) {
        db.createObjectStore('store1', { keyPath: 'id' });
    }
};

request.onsuccess = function(event) {
    console.log('數據庫成功打開');
};

request.onerror = function(event) {
    console.error('數據庫打開失敗', event);
};
```

### 示例 2：處理多個版本升級
```javascript
const request = indexedDB.open('multiVersionDB', 3);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const oldVersion = event.oldVersion;

    if (oldVersion < 1) {
        db.createObjectStore('store1', { keyPath: 'id' });
    }
    if (oldVersion < 2) {
        db.createObjectStore('store2', { keyPath: 'id' });
    }
    // 可能還有其他的版本處理
};

request.onsuccess = function(event) {
    console.log('數據庫成功打開');
};

request.onerror = function(event) {
    console.error('數據庫打開失敗', event);
};
```

## 解釋
### 常見陷阱
- **多次升級**：如果您在同一事件中對版本進行多次升級，請小心處理 `oldVersion` 和 `newVersion` 的邏輯，避免重複操作。
- **異步操作**：請注意，數據庫操作是異步的，確保在適當的事件中處理數據，避免在 `onsuccess` 中進行操作而未考慮到版本變更的情況。

### 額外注意事項
- 當數據庫版本升級時，舊版本的數據將不會被自動刪除，您需要根據需求手動進行清理。
- 確保在開發過程中定期測試版本變更的邏輯，以避免因架構變更導致的錯誤。

## 總結
`IDBVersionChangeEvent` 是一個關鍵的事件，允許開發者在 IndexedDB 中有效地管理數據庫版本變更，確保數據結構的穩定性和一致性。