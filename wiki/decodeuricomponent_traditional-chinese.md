<!--
Meta Description: # decodeURIComponent：JavaScript 中的 URL 解碼函數 ## 概述 `decodeURIComponent` 是一個 JavaScript 函數，用於將已編碼的 URI 組件解碼為可讀的字符串。這在處理 URL 時特別有用，因為許多字符在 URL 中需要進行編碼以確保...
Meta Keywords: decodeuricomponent, javascript, url, let, uri
-->

# decodeURIComponent：JavaScript 中的 URL 解碼函數

## 概述
`decodeURIComponent` 是一個 JavaScript 函數，用於將已編碼的 URI 組件解碼為可讀的字符串。這在處理 URL 時特別有用，因為許多字符在 URL 中需要進行編碼以確保正確傳遞。

## 文檔
### 目的
`decodeURIComponent` 主要用於將使用 `encodeURIComponent` 編碼的字符串進行解碼。它可以還原特殊字符（例如空格、斜線等）為其原始形式，以便於進一步處理和使用。

### 語法
```javascript
decodeURIComponent(encodedURIComponent);
```

### 參數
- `encodedURIComponent`：一個字符串，表示已編碼的 URI 組件。該字符串應包含由百分比（%）符號表示的 UTF-8 編碼字符。

### 返回值
返回解碼後的字符串。如果輸入的字符串無法正確解碼，則會拋出 `URIError`。

### 詳細說明
- `decodeURIComponent` 不會解碼百分比符號（%）本身。如果字符串中包含無效的百分比編碼，則會產生錯誤。
- 此函數通常與 `encodeURIComponent` 配對使用，以確保數據在 URL 中的正確傳遞。

## 範例
### 基本使用範例
```javascript
let encodedStr = "Hello%20World%21"; // 編碼字符串
let decodedStr = decodeURIComponent(encodedStr); // 解碼字符串
console.log(decodedStr); // 輸出: Hello World!
```

### 處理特殊字符
```javascript
let encodedUrl = "https%3A%2F%2Fwww.example.com%2Fsearch%3Fq%3DJavaScript%20%26%20SEO";
let decodedUrl = decodeURIComponent(encodedUrl);
console.log(decodedUrl); // 輸出: https://www.example.com/search?q=JavaScript & SEO
```

## 解釋
- **常見陷阱**：使用 `decodeURIComponent` 時，請確保字符串是正確編碼的。對於無效的編碼（例如 `%ZZ`），會拋出 `URIError`。
- **注意事項**：在處理用戶輸入的 URL 時，始終驗證和清理數據，以防止潛在的安全漏洞（如 XSS 攻擊）。

## 簡單總結
`decodeURIComponent` 是一個用於將已編碼的 URI 組件轉換回原始字符串的 JavaScript 函數。