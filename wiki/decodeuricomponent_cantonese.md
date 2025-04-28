<!--
Meta Description: # decodeURIComponent：JavaScript 中的解碼 URI 組件 ## 簡介 `decodeURIComponent` 是 JavaScript 中用於解碼經過 URI 編碼的字符串的內置函數。這個函數對於處理 URL 中的參數特別有用，因為它可以將百分比編碼（percent-...
Meta Keywords: decodeuricomponent, uri, javascript, const, url
-->

# decodeURIComponent：JavaScript 中的解碼 URI 組件

## 簡介
`decodeURIComponent` 是 JavaScript 中用於解碼經過 URI 編碼的字符串的內置函數。這個函數對於處理 URL 中的參數特別有用，因為它可以將百分比編碼（percent-encoded）格式的字符轉換回原始字符。

## 文檔
### 目的
`decodeURIComponent` 的主要目的是將經過 `encodeURIComponent` 編碼的字符串解碼回其原始形式，以便於進一步處理或顯示。

### 用法
`decodeURIComponent` 函數的語法如下：
```javascript
decodeURIComponent(encodedURI)
```
- **參數**：
  - `encodedURI`：一個經過 URI 編碼的字符串。

### 返回值
此函數返回一個字符串，該字符串是解碼後的結果。

### 詳細說明
`decodeURIComponent` 函數可以處理包括但不限於以下字符的解碼：
- 空格（%20）
- 特殊字符，如斜線（%2F）、問號（%3F）等

需要注意的是，這個函數不會解碼在 URI 中保留的特定字符，例如 `#`（hash）等，因為這些字符在 URI 中有特殊的意義。

## 範例
### 基本用法
以下是使用 `decodeURIComponent` 的一些基本範例：

```javascript
// 解碼一個簡單的 URI 組件
const encodedString = "Hello%20World%21";
const decodedString = decodeURIComponent(encodedString);
console.log(decodedString); // 輸出：Hello World!

// 解碼包含特殊字符的 URI
const encodedURL = "https%3A%2F%2Fwww.example.com%2Fsearch%3Fquery%3DJavaScript%2520decodeURIComponent";
const decodedURL = decodeURIComponent(encodedURL);
console.log(decodedURL); // 輸出：https://www.example.com/search?query=JavaScript%20decodeURIComponent
```

## 解釋
使用 `decodeURIComponent` 時，有幾個常見的陷阱：
- 確保傳入的字符串是有效的編碼字符串，否則可能會拋出 `URIError` 錯誤。
- 不要將已經解碼的字符串再次傳遞給這個函數，因為這樣可能會導致意外的結果或錯誤。
- `decodeURIComponent` 不會自動處理 URL 中的整個結構，只會針對提供的參數部分進行解碼。

## 一句總結
`decodeURIComponent` 是用於解碼經過 URI 編碼的字符串的 JavaScript 函數，幫助開發者輕鬆處理 URL 參數。