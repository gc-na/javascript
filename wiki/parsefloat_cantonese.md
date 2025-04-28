<!--
Meta Description: # JavaScript 中的 parseFloat：如何解析浮點數 ## 概述 `parseFloat` 是 JavaScript 中的一個全局函數，用於將字符串轉換為浮點數。這個函數非常適合處理數字數據的解析，特別是在從用戶輸入或其他來源獲取數據時。 ## 文檔 ### 目的 `parseFlo...
Meta Keywords: parsefloat, console, log, javascript, nan
-->

# JavaScript 中的 parseFloat：如何解析浮點數

## 概述
`parseFloat` 是 JavaScript 中的一個全局函數，用於將字符串轉換為浮點數。這個函數非常適合處理數字數據的解析，特別是在從用戶輸入或其他來源獲取數據時。

## 文檔
### 目的
`parseFloat` 的主要目的是將一個字符串轉換為浮點數。當字符串以數字開頭時，該函數會解析並返回該數字，並忽略字符串中後面的非數字字符。

### 使用方法
`parseFloat` 的語法如下：
```javascript
parseFloat(string);
```
- **參數**：
  - `string`：要解析的字符串。若傳入的參數不是字符串，將會自動轉換為字符串。
  
- **返回值**：
  - 返回解析后的浮點數。如果無法解析，則返回 `NaN`。

### 詳細信息
- `parseFloat` 會自動跳過字符串開頭的空格。
- 只會解析字符串中的數字部分，直到遇到無法解析的字符。
- 浮點數的格式遵循 IEEE 754 標準，支持正負號及科學記數法。

## 示例
### 基本用法
```javascript
console.log(parseFloat("3.14")); // 3.14
console.log(parseFloat("   42.5abc")); // 42.5
console.log(parseFloat("abc42.5")); // NaN
console.log(parseFloat("100.5E2")); // 10050
```

### 解析不同格式的字符串
```javascript
console.log(parseFloat("10.75")); // 10.75
console.log(parseFloat("  -20.25")); // -20.25
console.log(parseFloat("0.001")); // 0.001
```

## 解釋
### 常見陷阱
- 如果字符串不以數字開頭，`parseFloat` 將返回 `NaN`。例如，`parseFloat("abc123")` 會返回 `NaN`。
- `parseFloat` 不會報錯，即使傳入的字符串無法解析，這可能會使調試變得困難。
- 小心處理空字符串，因為 `parseFloat("")` 也會返回 `NaN`。

### 附加說明
- 對於整數的解析，使用 `parseInt` 可能更合適，但 `parseFloat` 對於浮點數的處理更加精確。
- 使用 `Number` 函數也可以將字符串轉換為數字，但它會對整個字符串進行評估，並且不會像 `parseFloat` 一樣忽略後面的非數字字符。

## 一句總結
`parseFloat` 是 JavaScript 中用於將字符串轉換為浮點數的函數，並能夠靈活處理數字和非數字字符。