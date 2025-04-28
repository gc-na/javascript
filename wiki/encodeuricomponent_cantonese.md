<!--
Meta Description: # 使用 JavaScript 的 encodeURIComponent 函數進行 URL 編碼 ## 概述 `encodeURIComponent` 是一個 JavaScript 函數，用於對 URI 組件進行編碼，以便安全地在 URL 中傳輸數據。它能夠將特殊字符轉換為百分比編碼，以避免在網絡請...
Meta Keywords: encodeuricomponent, url, javascript, uri, const
-->

# 使用 JavaScript 的 encodeURIComponent 函數進行 URL 編碼

## 概述
`encodeURIComponent` 是一個 JavaScript 函數，用於對 URI 組件進行編碼，以便安全地在 URL 中傳輸數據。它能夠將特殊字符轉換為百分比編碼，以避免在網絡請求中出現錯誤。

## 文檔
### 目的
`encodeURIComponent` 的主要目的是對 URI 的組件進行編碼，確保其在 URL 中的有效性。當某些字符（如空格、斜線、問號等）出現在 URL 中時，這些字符可能會干擾數據的正確解析。

### 使用方法
`encodeURIComponent` 函數接受一個字符串作為參數，並返回一個編碼后的字符串。語法如下：

```javascript
encodeURIComponent(string)
```

- **參數**：
  - `string`：需要編碼的字符串。

- **返回值**：
  - 返回一個編碼后的字符串，其中所有非字母數字字符和一些特殊字符都被轉換為百分比編碼的格式。

### 詳細說明
`encodeURIComponent` 函數會將以下字符進行編碼：
- 所有非字母數字字符
- 特殊字符，如空格（變為 `%20`），斜線（變為 `%2F`），問號（變為 `%3F`），等號（變為 `%3D`）等。

這個函數特別適合用於編碼 URL 的查詢字符串或路徑組件。

## 範例
以下是 `encodeURIComponent` 的基本用法示例：

```javascript
const paramName = "name";
const paramValue = "John Doe & Co.";
const encodedParam = encodeURIComponent(paramName + '=' + paramValue);

console.log(encodedParam); // 輸出: name=John%20Doe%20%26%20Co.
```

在這個例子中，`"John Doe & Co."` 中的空格和 `&` 符號都被正確地編碼成 `%20` 和 `%26`。

## 解釋
### 常見陷阱
- **不要與 `encodeURI` 混淆**：`encodeURI` 用於編碼整個 URI，而不會編碼某些特殊字符（如 `:`, `/`, `?`, `&` 等），而 `encodeURIComponent` 則會編碼所有特殊字符。
- **多次編碼**：避免對已經編碼的字符串再次使用 `encodeURIComponent`，這會導致不必要的冗餘編碼。

### 附註
在處理用戶輸入數據或從 API 獲取的數據時，使用 `encodeURIComponent` 是一個良好的習慣，這樣可以有效避免因特殊字符導致的潛在問題。

## 一句總結
`encodeURIComponent` 是一個用於將 URI 組件進行編碼的 JavaScript 函數，以確保這些組件能夠安全地在 URL 中傳輸。