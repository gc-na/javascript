<!--
Meta Description: # JavaScript 中的錯誤（Error）處理指南 ## 簡介 在 JavaScript 中，錯誤（Error）是指在執行程式碼時出現的異常情況。有效的錯誤處理對於提升應用程序的穩定性和用戶體驗至關重要。 ## 文檔 ### 目的 JavaScript 提供了一個內建的錯誤對象，允許開發者捕獲...
Meta Keywords: error, javascript, try, catch, message
-->

# JavaScript 中的錯誤（Error）處理指南

## 簡介
在 JavaScript 中，錯誤（Error）是指在執行程式碼時出現的異常情況。有效的錯誤處理對於提升應用程序的穩定性和用戶體驗至關重要。

## 文檔
### 目的
JavaScript 提供了一個內建的錯誤對象，允許開發者捕獲和處理執行期間的錯誤。這有助於及時識別問題並防止應用程序崩潰。

### 使用方式
在 JavaScript 中，錯誤對象可以通過 `try...catch` 語句來捕獲。基本語法如下：

```javascript
try {
    // 可能產生錯誤的代碼
} catch (error) {
    // 錯誤處理代碼
}
```

### 詳細說明
- **Error 類別**: JavaScript 提供了 `Error` 類別以及其子類別（如 `TypeError`, `SyntaxError`, `ReferenceError` 等），這些類別用於表示不同類型的錯誤。
- **屬性**: 錯誤對象通常包含以下屬性：
  - `name`: 錯誤的名稱。
  - `message`: 錯誤的描述信息。
  - `stack`: 錯誤發生時的堆棧跟蹤信息。
  
- **自定義錯誤**: 開發者可以擴展 `Error` 類來創建自定義錯誤類別，用於特定的錯誤處理需求。

## 範例
### 基本使用範例
```javascript
try {
    // 嘗試執行可能出現錯誤的代碼
    let result = someUndefinedFunction();
} catch (error) {
    console.error("發生錯誤: ", error.message);
}
```

### 自定義錯誤範例
```javascript
class CustomError extends Error {
    constructor(message) {
        super(message);
        this.name = "CustomError";
    }
}

try {
    throw new CustomError("這是一個自定義錯誤");
} catch (error) {
    console.error(`${error.name}: ${error.message}`);
}
```

## 解釋
- **常見陷阱**: 使用 `try...catch` 時，確保捕獲的錯誤不會被忽略。忽略錯誤可能會導致難以調試的問題。
- **性能影響**: 雖然使用 `try...catch` 是安全的，但過度使用可能影響性能，特別是在頻繁調用的代碼塊中。
- **錯誤傳遞**: 在大型應用程序中，考慮使用全局錯誤處理器來統一處理錯誤，提升維護性。

## 一句總結
JavaScript 的錯誤處理機制透過 `try...catch` 語句和錯誤對象，幫助開發者捕獲和處理執行期間的異常，從而提高應用程序的穩定性。