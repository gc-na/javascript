<!--
Meta Description: # FinalizationRegistry：JavaScript 中的物件釋放管理機制 ## 簡介 `FinalizationRegistry` 是一個 JavaScript API，旨在幫助開發者在物件被垃圾回收（Garbage Collection）後進行清理操作。這對於需要釋放資源或執行特定...
Meta Keywords: finalizationregistry, key, value, javascript, callback
-->

# FinalizationRegistry：JavaScript 中的物件釋放管理機制

## 簡介
`FinalizationRegistry` 是一個 JavaScript API，旨在幫助開發者在物件被垃圾回收（Garbage Collection）後進行清理操作。這對於需要釋放資源或執行特定清理任務的情況非常有用。

## 文檔
### 目的
`FinalizationRegistry` 提供了一種方法來註冊回調函數，當與註冊的物件關聯的記憶體被釋放時將會呼叫這些函數。這對於管理需要在物件生命週期結束時進行的資源釋放特別重要。

### 使用方法
要使用 `FinalizationRegistry`，需要遵循以下步驟：

1. **創建 FinalizationRegistry 實例**：
   使用 `new FinalizationRegistry(callback)` 來創建一個新的 `FinalizationRegistry` 實例，其中 `callback` 是在物件被垃圾回收時呼叫的函數。

2. **註冊物件**：
   使用 `register(value, key)` 方法來註冊一個物件，`value` 是要註冊的物件，`key` 是一個標識符，用於在回調函數中識別該物件。

3. **回調函數**：
   當註冊的物件被垃圾回收時，提供的回調函數將會被呼叫，並傳遞之前註冊的 `key`。

### 詳細說明
- **構造函數**：`FinalizationRegistry(callback)`，其中 `callback` 是一個函數，接受一個參數，該參數是先前註冊的 `key`。
  
- **方法**：
  - `register(value, key)`：註冊一個物件 `value` 和一個標識符 `key`。當 `value` 被垃圾回收時，`callback` 將會被呼叫並傳遞 `key`。
  - **注意**：`value` 必須是一個物件；如果 `value` 是原始類型，則會拋出錯誤。

- **垃圾回收行為**：在 JavaScript 中，垃圾回收是非同步的，因此不能保證何時會發生。這意味著回調的執行時間可能會有所不同。

## 範例
```javascript
// 創建 FinalizationRegistry 實例
const registry = new FinalizationRegistry((key) => {
    console.log(`${key} 物件已被垃圾回收`);
});

// 註冊物件
let obj = {};
registry.register(obj, 'myObject');

// 清除對物件的引用
obj = null;

// 在未來的某個時刻，垃圾回收可能會發生
// Console 可能會顯示： "myObject 物件已被垃圾回收"
```

## 說明
- **常見問題**：
  - 無法確定回調何時會被調用：因為垃圾回收的運行時機不確定，所以回調可能不會立即執行。
  - 不應依賴 `FinalizationRegistry` 來管理重要的應用邏輯，因為回調執行的時間是不可預測的。

- **注意事項**：
  - `FinalizationRegistry` 並不是一個替代物件的析構函數。它主要用於當物件不再需要時進行清理操作。
  - 註冊過多的回調可能會影響性能，因此應謹慎使用。

## 一句總結
`FinalizationRegistry` 是 JavaScript 中用於管理物件垃圾回收後的資源釋放的有效工具。