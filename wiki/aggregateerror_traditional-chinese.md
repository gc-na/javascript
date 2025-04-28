<!--
Meta Description: # AggregateError：JavaScript 中的聚合錯誤 ## 概述 `AggregateError` 是 JavaScript 中一種用於表示多個錯誤的錯誤類型，特別是在處理 Promise 的情況下。它可以將多個錯誤整合到一個錯誤物件中，便於開發者更高效地處理異常情況。 ## 文檔 ...
Meta Keywords: aggregateerror, promise, javascript, any, new
-->

# AggregateError：JavaScript 中的聚合錯誤

## 概述
`AggregateError` 是 JavaScript 中一種用於表示多個錯誤的錯誤類型，特別是在處理 Promise 的情況下。它可以將多個錯誤整合到一個錯誤物件中，便於開發者更高效地處理異常情況。

## 文檔
### 目的
`AggregateError` 的主要用途是將多個錯誤聚合到一個物件中，特別是在進行 Promise 操作時。這樣，開發者可以一次性捕獲並處理多個錯誤，而不必單獨處理每個錯誤。

### 使用方式
`AggregateError` 是一個內建的錯誤類型，通常與 `Promise.any()` 方法一起使用。當傳遞給 `Promise.any()` 的所有 Promise 都被拒絕時，將返回一個 `AggregateError`。

#### 語法
```javascript
new AggregateError(errors, message);
```

- `errors`：一個包含多個錯誤物件的可迭代對象，例如一個陣列。
- `message`：一個可選的字串，用於描述錯誤的內容。

### 屬性
- `errors`：返回一個包含所有聚合錯誤的陣列。
- `name`：該錯誤的名稱，為 `AggregateError`。

## 示例
### 基本用法
以下是一個使用 `AggregateError` 的簡單範例：

```javascript
async function fetchData() {
    const promises = [
        Promise.reject(new Error("錯誤1")),
        Promise.reject(new Error("錯誤2")),
        Promise.reject(new Error("錯誤3"))
    ];

    try {
        await Promise.any(promises);
    } catch (e) {
        if (e instanceof AggregateError) {
            console.log("捕獲到多個錯誤:");
            e.errors.forEach(err => console.log(err.message));
        } else {
            console.log("發生其他錯誤:", e);
        }
    }
}

fetchData();
```

在這個例子中，`Promise.any()` 會拒絕所有的 Promise，進而觸發 `AggregateError`，我們可以輕鬆地列出所有的錯誤訊息。

## 解釋
### 常見陷阱
- **未處理的錯誤**：如果沒有正確處理 `AggregateError`，可能會導致應用程式崩潰。應確保在 `catch` 區塊中進行正確的錯誤檢查。
- **錯誤類型**：使用 `instanceof` 檢查錯誤類型是捕獲 `AggregateError` 的最佳方法，以確保其他錯誤不會被誤判。

### 附加說明
使用 `AggregateError` 可以提高錯誤處理的靈活性，特別是在處理大量的異步請求時。它允許開發者更清晰地管理錯誤，並提供更好的用戶體驗。

## 單行總結
`AggregateError` 是一種聚合多個錯誤的錯誤類型，用於簡化 Promise 錯誤處理。