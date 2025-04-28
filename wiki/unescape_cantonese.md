<!--
Meta Description: # JavaScript 中的 unescape 函數：用於解碼 URI 的工具 ## 概述 `unescape` 函數是 JavaScript 中的一個舊有方法，主要用於解碼之前用 `escape` 函數編碼的字符串。雖然這個函數在早期的網頁開發中十分常用，但隨著時間的推移，它已經不再建議使用。取...
Meta Keywords: unescape, javascript, escape, decodeuri, decodeuricomponent
-->

# JavaScript 中的 unescape 函數：用於解碼 URI 的工具

## 概述
`unescape` 函數是 JavaScript 中的一個舊有方法，主要用於解碼之前用 `escape` 函數編碼的字符串。雖然這個函數在早期的網頁開發中十分常用，但隨著時間的推移，它已經不再建議使用。取而代之的是 `decodeURI` 和 `decodeURIComponent` 函數。

## 文檔
### 目的
`unescape` 函數的主要目的是將經過 `escape` 編碼的字符串解碼回其原始字符。

### 用法
`unescape` 函數的語法如下：
```javascript
unescape(str);
```
- **參數**：`str` - 需要被解碼的字符串，通常是用 `escape` 編碼的字符串。
- **返回值**：返回解碼後的字符串。

### 詳細說明
`unescape` 函數會將字符串中的十六進制編碼（如 `%xx`）轉換回對應的字符。例如，`%20` 會被轉換為空格字符。需要注意的是，`unescape` 只支持某些特定的字符編碼，並且對於某些非 ASCII 字符可能無法正確解碼。

由於 `unescape` 已經過時，建議使用 `decodeURI` 和 `decodeURIComponent`，這些函數提供了更強大的功能，並且可以處理更廣泛的字符編碼。

## 範例
以下是 `unescape` 函數的基本用法示例：

```javascript
// 示例 1：基本使用
var encodedString = "Hello%20World%21"; // 用 escape 編碼的字符串
var decodedString = unescape(encodedString);
console.log(decodedString); // 輸出：Hello World!

// 示例 2：解碼特殊字符
var specialEncodedString = "C%2B%2B%20is%20great%21";
var specialDecodedString = unescape(specialEncodedString);
console.log(specialDecodedString); // 輸出：C++ is great!
```

## 解釋
### 常見陷阱
1. **過時的函數**：`unescape` 函數已經被標記為不建議使用。建議使用 `decodeURI` 或 `decodeURIComponent`，因為它們能更好地處理現代的 URI 編碼。
2. **字符集問題**：`unescape` 只支援某些編碼，對於 UTF-8 等多字節字符編碼不會正確解碼，這可能導致出現不可預期的錯誤。
3. **安全性考慮**：使用 `unescape` 可能導致安全風險，例如 XSS 攻擊，因為它不會自動處理某些潛在的危險字符。

## 一句總結
`unescape` 函數是 JavaScript 中一個過時的字符串解碼工具，已不再建議使用，應以 `decodeURI` 和 `decodeURIComponent` 替代。