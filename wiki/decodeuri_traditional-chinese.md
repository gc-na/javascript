<!--
Meta Description: # JavaScript 中的 decodeURI 函數：解碼 URI 結構 ## 簡介 `decodeURI` 是 JavaScript 中的一個內建函數，用於解碼經過 URI 編碼的字串。它能將使用 `encodeURI` 或類似方法編碼後的 URI 字串轉換回原始的可讀格式。 ## 文檔 ##...
Meta Keywords: uri, decodeuri, javascript, encodeduri, let
-->

# JavaScript 中的 decodeURI 函數：解碼 URI 結構

## 簡介
`decodeURI` 是 JavaScript 中的一個內建函數，用於解碼經過 URI 編碼的字串。它能將使用 `encodeURI` 或類似方法編碼後的 URI 字串轉換回原始的可讀格式。

## 文檔
### 目的
`decodeURI` 函數的主要用途是解碼包含特殊字符的 URI 字串，這些字符在 URI 中通常會被編碼為百分比格式（例如，空格會被編碼為 `%20`）。這使得 URI 可以安全地在網絡中傳輸。

### 語法
```javascript
decodeURI(encodedURI)
```

### 參數
- `encodedURI`：要解碼的 URI 字串，必須是有效的 URI 編碼格式。

### 返回值
`decodeURI` 返回一個解碼後的字串，該字串的內容與原始字串相同，但所有的百分比編碼字符都會被轉換回其對應的字符。

### 使用範例
```javascript
// 示例 1：解碼一個簡單的 URI
let encodedURI = "https%3A%2F%2Fwww.example.com%2Fhello%20world";
let decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // 輸出: https://www.example.com/hello world

// 示例 2：解碼包含多個特殊字符的 URI
let anotherEncodedURI = "https%3A%2F%2Fwww.example.com%2Fsearch%3Fq%3DJavaScript%20%E8%AA%9E%E8%A8%80";
let anotherDecodedURI = decodeURI(anotherEncodedURI);
console.log(anotherDecodedURI); // 輸出: https://www.example.com/search?q=JavaScript 語言
```

## 解釋
在使用 `decodeURI` 時，開發者應注意以下幾點：
- `decodeURI` 不會解碼某些字符，例如 `#`、`?` 和 `&`，因為這些字符在 URI 中具有特殊的意義。
- 如果輸入的 URI 字串不符合編碼規則，`decodeURI` 會拋出 `URIError` 錯誤。因此，確保用於解碼的字串是正確編碼的非常重要。
- 對於需要解碼單個組件的情況，可以使用 `decodeURIComponent` 函數，該函數會解碼所有的百分比編碼字符。

## 總結
`decodeURI` 是 JavaScript 中用於解碼 URI 的有效工具，能幫助開發者將編碼的字串還原為可讀格式。