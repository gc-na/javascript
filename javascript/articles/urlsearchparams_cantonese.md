<!--
Meta Description: # URLSearchParams：JavaScript 中的 URL 查詢參數處理工具 ## 概述 `URLSearchParams` 是一個用於處理 URL 查詢參數的 JavaScript 內建對象。它提供了一個簡單的 API 來讀取、修改和生成 URL 查詢字符串，特別適合用於處理 GET ...
Meta Keywords: urlsearchparams, name, params, javascript, url
-->

# URLSearchParams：JavaScript 中的 URL 查詢參數處理工具

## 概述
`URLSearchParams` 是一個用於處理 URL 查詢參數的 JavaScript 內建對象。它提供了一個簡單的 API 來讀取、修改和生成 URL 查詢字符串，特別適合用於處理 GET 請求中的參數。

## 文檔

### 目的
`URLSearchParams` 的主要目的是簡化 URL 查詢參數的操作，讓開發者能夠輕鬆地獲取和修改這些參數，而不需要手動解析字符串。

### 用法
要使用 `URLSearchParams`，您可以按照以下步驟進行：

1. 創建一個 `URLSearchParams` 對象，並將查詢字符串作為參數傳遞。
2. 使用內建的方法來讀取和操作參數。

#### 主要方法
- `get(name)`：獲取指定名稱的參數值。
- `set(name, value)`：設置指定名稱的參數值。
- `append(name, value)`：追加一個新的參數值。
- `delete(name)`：刪除指定名稱的參數。
- `has(name)`：檢查是否存在指定名稱的參數。

### 建立對象
```javascript
const params = new URLSearchParams('name=John&age=30');
```

## 示例

### 基本用法
```javascript
// 創建 URLSearchParams 對象
const params = new URLSearchParams('name=John&age=30');

// 獲取參數值
console.log(params.get('name')); // 輸出: John
console.log(params.get('age')); // 輸出: 30

// 設置參數值
params.set('age', 31);
console.log(params.get('age')); // 輸出: 31

// 追加參數值
params.append('hobby', 'reading');
console.log(params.getAll('hobby')); // 輸出: ["reading"]

// 刪除參數
params.delete('name');
console.log(params.has('name')); // 輸出: false
```

## 解釋

### 常見問題
- **不支持的瀏覽器**：`URLSearchParams` 在 IE11 及以下版本不受支持，開發者需考慮兼容性問題。
- **參數編碼**：當參數中包含特殊字符（如空格、符號等）時，應確保進行正確的編碼和解碼，以避免錯誤。

### 注意事項
- `URLSearchParams` 只支持 UTF-8 字符集。
- 使用 `append` 方法可以添加多個相同名稱的參數，而 `set` 方法則會替換原有的值。

## 一句總結
`URLSearchParams` 是一個強大的工具，使得在 JavaScript 中處理 URL 查詢參數變得簡單而高效。