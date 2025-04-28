<!--
Meta Description: # parseFloat：JavaScript 中的浮點數解析函數 ## 摘要 `parseFloat` 是一個用於將字符串轉換為浮點數的 JavaScript 函數，能夠解析並返回一個指定的浮點數值。 ## 文檔 `parseFloat` 函數的主要目的是從字符串中提取數字，並將其轉換為浮點數類型...
Meta Keywords: parsefloat, console, log, javascript, nan
-->

# parseFloat：JavaScript 中的浮點數解析函數

## 摘要
`parseFloat` 是一個用於將字符串轉換為浮點數的 JavaScript 函數，能夠解析並返回一個指定的浮點數值。

## 文檔
`parseFloat` 函數的主要目的是從字符串中提取數字，並將其轉換為浮點數類型。這個函數會解析字符串中的數字，直到遇到非數字字符為止。它的語法如下：

```javascript
parseFloat(string);
```

### 參數
- **string**：要解析的字符串，這個參數是必需的。

### 返回值
- 返回解析後的浮點數。如果字符串的開頭不是數字或空字符串，則返回 `NaN`（不是一個數字）。

## 範例
以下是一些 `parseFloat` 的基本用法範例：

```javascript
console.log(parseFloat("3.14"));          // 輸出：3.14
console.log(parseFloat("10.99abc"));      // 輸出：10.99
console.log(parseFloat("abc10.99"));      // 輸出：NaN
console.log(parseFloat("  42  "));        // 輸出：42
console.log(parseFloat("0.1e3"));         // 輸出：100
```

## 解釋
在使用 `parseFloat` 時，開發者應該注意以下幾點：

1. **非數字字符**：當字符串中包含非數字字符時，`parseFloat` 只會解析到第一個非數字字符為止。例如，`parseFloat("10.5abc")` 會返回 `10.5`。

2. **空字符串**：如果傳入的字符串為空，則返回 `NaN`，例如 `parseFloat("")`。

3. **空格處理**：`parseFloat` 會自動忽略字符串開頭和結尾的空格。

4. **科學記數法**：`parseFloat` 能夠處理科學記數法表示的數字，例如 `"1e3"` 會被解析為 `1000`。

5. **返回值類型**：注意返回值類型，如果無法解析出有效數字，將返回 `NaN`，此時可以使用 `isNaN` 函數來檢查。

## 總結
`parseFloat` 是一個用於將字符串轉換為浮點數的有用函數，能有效解析數字並處理多種格式。