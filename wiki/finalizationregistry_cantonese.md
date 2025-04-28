<!--
Meta Description: # FinalizationRegistry：JavaScript 中的對象追蹤與清理機制 ## 概述 `FinalizationRegistry` 是 JavaScript 中的一個內建對象，用於追蹤對象的最終清理。當一個對象被垃圾回收時，`FinalizationRegistry` 允許註冊一個...
Meta Keywords: finalizationregistry, javascript, registry, heldvalue, register
-->

# FinalizationRegistry：JavaScript 中的對象追蹤與清理機制

## 概述
`FinalizationRegistry` 是 JavaScript 中的一個內建對象，用於追蹤對象的最終清理。當一個對象被垃圾回收時，`FinalizationRegistry` 允許註冊一個回調函數，以便在對象被垃圾回收後執行某些清理操作。

## 文檔
### 目的
`FinalizationRegistry` 主要用於管理資源的清理，特別是在需要跟蹤的對象被釋放後，能夠進行必要的清理工作，從而避免內存洩漏。

### 使用方法
要使用 `FinalizationRegistry`，首先需要創建一個 `FinalizationRegistry` 實例並傳入一個回調函數。這個回調函數將在對象被垃圾回收後被調用。

#### 語法
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    // 在對象被垃圾回收時執行的代碼
});
```

#### 註冊對象
使用 `register` 方法來註冊一個對象，並將其和一個持有的值關聯起來。

```javascript
registry.register(object, heldValue);
```

#### 解除註冊
如果不再需要追蹤某個對象，可以使用 `unregister` 方法來解除註冊。

```javascript
registry.unregister(object);
```

## 範例
```javascript
// 創建 FinalizationRegistry 實例
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`對象被垃圾回收，持有值是：${heldValue}`);
});

// 註冊對象
let obj = {};
registry.register(obj, '這是持有的值');

// 釋放對象
obj = null;

// 強制執行垃圾回收（僅在某些環境中可用）
if (globalThis.gc) {
    globalThis.gc();
}
```

## 解釋
### 常見問題
- **回調的執行時間**：當對象被垃圾回收時，回調函數並不會立即執行，其執行時間是不可預測的。
- **持有值的引用**：持有值不應該持有對被註冊對象的引用，否則該對象將不會被垃圾回收。
- **不保證執行**：如果 JavaScript 引擎不進行垃圾回收，則回調函數可能永遠不會被調用。

### 注意事項
- `FinalizationRegistry` 主要用於需要在對象被釋放後執行清理的場景，例如在處理大型數據結構或網絡資源時。
- 應謹慎使用，以避免影響性能，因為垃圾回收的頻率和回調的執行時間都是不確定的。

## 一句總結
`FinalizationRegistry` 是一個用於追蹤對象垃圾回收後的清理操作的 JavaScript 機制。