<!--
Meta Description: # JavaScript 中的 escape 函数：用於編碼特殊字符 ## 簡介 在 JavaScript 中，`escape` 函數是一個用來編碼字符串中的特殊字符的函數。它將字符轉換為可以在 URL 中安全使用的格式，以便在互聯網上傳遞。 ## 文檔 ### 目的 `escape` 函數的主要目...
Meta Keywords: escape, javascript, url, ascii, string
-->

# JavaScript 中的 escape 函数：用於編碼特殊字符

## 簡介
在 JavaScript 中，`escape` 函數是一個用來編碼字符串中的特殊字符的函數。它將字符轉換為可以在 URL 中安全使用的格式，以便在互聯網上傳遞。

## 文檔
### 目的
`escape` 函數的主要目的是將字符串中的非 ASCII 字符轉換為十六進制表示法，以避免在 URL 或其他需要安全傳輸的情況下出現問題。

### 使用方法
語法如下：
```javascript
escape(string)
```
- **參數**：
  - `string`：要被編碼的字符串。

- **返回值**：返回一個編碼後的字符串，所有非 ASCII 字符都將被轉換。

### 詳細說明
`escape` 函數可以處理大多數字符，但它並不適用於所有情況。值得注意的是，這個函數已經被標記為不推薦使用，因為它無法正確處理某些字符，特別是 Unicode 字符。取而代之，建議使用 `encodeURIComponent` 或 `encodeURI` 函數來進行更安全的編碼。

## 範例
以下是使用 `escape` 函數的基本示例：

```javascript
let str = "Hello, 世界!";
let encodedStr = escape(str);
console.log(encodedStr); // 輸出：Hello%2C%20%u4E16%u754C%21
```

在這個例子中，字符串中的中文字符「世界」被轉換為其對應的 Unicode 表示。

## 解釋
- **常見陷阱**：`escape` 函數不能處理所有的字符，特別是像 `+` 和 `@` 等字符將不會被編碼，這可能會導致一些意外的錯誤。
- **不推薦使用**：由於 `escape` 函數的局限性，建議使用 `encodeURIComponent` 或 `encodeURI` 來替代。

## 一句總結
`escape` 函數在 JavaScript 中用於編碼字符串中的特殊字符，但由於其局限性，應考慮使用更新的編碼方法。