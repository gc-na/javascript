<!--
Meta Description: # JavaScript 中的 parseInt 函數詳解 ## 概述 `parseInt` 是一個 JavaScript 的內建函數，用於將字符串解析為整數。此函數在處理數據類型轉換時非常有用，特別是在處理用戶輸入或從外部數據源獲取的字符串時。 ## 文檔 ### 目的 `parseInt` 函數...
Meta Keywords: parseint, console, log, javascript, nan
-->

# JavaScript 中的 parseInt 函數詳解

## 概述
`parseInt` 是一個 JavaScript 的內建函數，用於將字符串解析為整數。此函數在處理數據類型轉換時非常有用，特別是在處理用戶輸入或從外部數據源獲取的字符串時。

## 文檔
### 目的
`parseInt` 函數的主要目的是將一個字符串轉換為整數，並支持指定進制（基數）。它可以用於解析整數值，並且在需要將數字以字符串形式存儲時非常方便。

### 使用方法
```javascript
parseInt(string, radix);
```
- **string**: 要解析的字符串。
- **radix**: 一個可選的整數，代表基數（進制），範圍是 2 到 36。如果省略，則根據字符串的內容自動推斷進制。

### 詳細說明
- `parseInt` 會從字符串的開始處解析字符，直到遇到無法識別的字符為止。
- 如果字符串的開頭是空白字符，這些空白字符會被忽略。
- 若字符串以非數字字符開始，則返回 `NaN`（不是一個數字）。
- 當指定 `radix` 時，`parseInt` 會根據這個基數解析字符串。

## 例子
以下是一些使用 `parseInt` 的基本範例：

```javascript
console.log(parseInt("123"));          // 123
console.log(parseInt("123.45"));       // 123
console.log(parseInt("0xF", 16));      // 15
console.log(parseInt("1010", 2));      // 10
console.log(parseInt("abc"));          // NaN
console.log(parseInt("  42  "));       // 42
```

## 解釋
### 常見陷阱
1. **基數的影響**: 如果未指定基數，`parseInt` 可能會根據字符串的內容自動選擇基數。這可能導致意外行為，例如 `"012"` 在某些環境中會被解析為 10 而不是 12。
  
2. **NaN 的處理**: 當解析不成功時，`parseInt` 返回 `NaN`。在進行數字計算之前，應檢查返回值是否為 `NaN`。

3. **小數部分的丟失**: `parseInt` 僅返回整數部分，會忽略小數部分。

### 額外提示
- 在解析十進制數字時，建議明確指定基數為 10，這樣可以避免不必要的混淆。
- 使用 `Number` 函數或 `parseFloat` 來處理浮點數。

## 總結
`parseInt` 函數是一個強大的工具，用於在 JavaScript 中將字符串轉換為整數，並支持多種進制的解析。