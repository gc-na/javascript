<!--
Meta Description: # AggregateError 在 JavaScript 的應用與特性 ## 簡介 `AggregateError` 是 JavaScript 中一種用來表示多個錯誤的錯誤類型，特別是在處理 Promise 時發生多個錯誤的情況。這個功能在 ES2021（ES12）中被引入，旨在讓錯誤處理更為靈活...
Meta Keywords: aggregateerror, promise, error, new, javascript
-->

# AggregateError 在 JavaScript 的應用與特性

## 簡介
`AggregateError` 是 JavaScript 中一種用來表示多個錯誤的錯誤類型，特別是在處理 Promise 時發生多個錯誤的情況。這個功能在 ES2021（ES12）中被引入，旨在讓錯誤處理更為靈活和高效。

## 文檔
### 目的
`AggregateError` 允許開發者收集並處理來自多個 Promise 的錯誤，並將它們封裝在一個單一的錯誤對象中，從而簡化錯誤處理的流程。

### 用法
`AggregateError` 的用法相當直觀，開發者可以在捕獲錯誤時創建一個 `AggregateError` 對象，並將多個錯誤作為參數傳遞給它。

```javascript
const errors = [
  new Error("錯誤 1"),
  new Error("錯誤 2"),
  new Error("錯誤 3")
];

const aggregateError = new AggregateError(errors, "多個錯誤發生");
```

### 詳細說明
- **構造函數**：`AggregateError` 的構造函數接收兩個參數：
  1. `errors`：一個錯誤對象的可迭代對象（例如數組）。
  2. `message`：可選的字符串，描述錯誤的內容。
  
- **屬性**：
  - `errors`：返回一個包含所有錯誤的數組。
  - `message`：返回錯誤信息。
  
- **用途場景**：在同時處理多個 Promise 時，若其中任一個 Promise 拋出錯誤，開發者可以使用 `AggregateError` 來捕獲所有錯誤，而不是僅僅捕獲第一個錯誤。

## 示例
以下是一個使用 `AggregateError` 的基本範例：

```javascript
async function fetchData() {
  const promises = [
    Promise.resolve("數據 1"),
    Promise.reject(new Error("數據載入錯誤")),
    Promise.resolve("數據 2"),
    Promise.reject(new Error("數據載入錯誤 2"))
  ];

  try {
    const results = await Promise.all(promises);
    console.log(results);
  } catch (error) {
    if (error instanceof AggregateError) {
      console.log("發生了多個錯誤：");
      error.errors.forEach(err => console.log(err.message));
    } else {
      console.log("其他錯誤：", error.message);
    }
  }
}

fetchData();
```

## 解釋
### 常見問題
- **只捕獲第一個錯誤**：使用傳統的 Promise 錯誤處理（如 `.catch`）時，通常只會捕獲第一個錯誤，而 `AggregateError` 可以捕獲所有錯誤。
- **兼容性問題**：在某些舊版本的 JavaScript 環境中，`AggregateError` 可能不被支持，因此在使用前需要檢查瀏覽器的兼容性。

### 附註
- 在處理大量 Promise 時，使用 `AggregateError` 可以有效地減少錯誤處理的複雜性。
- 針對每一個 Promise 的錯誤進行獨立處理能提高代碼的可讀性和維護性。

## 總結
`AggregateError` 是一個強大的工具，可以幫助開發者同時處理多個 Promise 錯誤，從而提升錯誤處理的靈活性和效率。