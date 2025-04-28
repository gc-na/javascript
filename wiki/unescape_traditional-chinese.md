<!--
Meta Description: # JavaScript 中的 unescape 函數：解碼 URL 字符串的工具 ## 概述 `unescape` 是 JavaScript 中的一個全局函數，用於解碼已經被 `escape` 函數編碼的字符串。它的主要用途是在處理 URL 字符串時，將被轉義的字符還原為可讀格式。然而，值得注意的...
Meta Keywords: unescape, javascript, url, escape, str
-->

# JavaScript 中的 unescape 函數：解碼 URL 字符串的工具

## 概述
`unescape` 是 JavaScript 中的一個全局函數，用於解碼已經被 `escape` 函數編碼的字符串。它的主要用途是在處理 URL 字符串時，將被轉義的字符還原為可讀格式。然而，值得注意的是，這個函數已經被標記為不推薦使用，並且在未來的版本中可能會被移除。

## 文檔
### 目的
`unescape` 函數的主要目的是將字符串中的轉義序列（如 `%20` 代表空格）轉換回其原始字符。這在處理 URL 或其他需要編碼的字符串時非常有用。

### 語法
```javascript
unescape(str)
```

### 參數
- `str`：要解碼的字符串，該字符串應該是由 `escape` 函數編碼的。

### 返回值
- 返回一個新的字符串，其中所有的轉義序列都被替換為對應的字符。

## 示例
以下是 `unescape` 的基本用法範例：

```javascript
// 使用 unescape 解碼字符串
let encodedStr = "Hello%20World%21";
let decodedStr = unescape(encodedStr);
console.log(decodedStr); // 輸出：Hello World!
```

## 解釋
### 常見問題
1. **不推薦使用**：`unescape` 函數已被標記為不推薦使用（deprecated），因為它並不支持所有的 Unicode 編碼，並且在處理某些字符時可能會產生意想不到的結果。開發者應優先考慮使用 `decodeURIComponent` 函數。
   
2. **不支持的字符**：`unescape` 只支持 ASCII 字符，對於非 ASCII 字符（如中文、日文等）會出現解碼錯誤。

3. **替代方案**：使用 `decodeURIComponent` 來解碼 URL 字符串是更安全、更通用的做法。

## 總結
`unescape` 是一個用於解碼被轉義字符串的 JavaScript 函數，儘管它在某些情況下仍然可用，但因為不推薦使用而不應被視為最佳實踐。