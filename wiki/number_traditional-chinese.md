<!--
Meta Description: # JavaScript 數字 (Number) 類型介紹 ## 摘要 在 JavaScript 中，數字 (Number) 是一個基本數據類型，代表整數和浮點數，並且支援多種數學運算。JavaScript 的數字類型使用 IEEE 754 雙精度浮點數格式，這使得它能夠處理非常大或非常小的數值。 ...
Meta Keywords: javascript, let, number, nan, console
-->

# JavaScript 數字 (Number) 類型介紹

## 摘要
在 JavaScript 中，數字 (Number) 是一個基本數據類型，代表整數和浮點數，並且支援多種數學運算。JavaScript 的數字類型使用 IEEE 754 雙精度浮點數格式，這使得它能夠處理非常大或非常小的數值。

## 文檔
### 目的
JavaScript 的數字類型主要用於數學計算、數據處理及各種計算需求。它支持基本的算術運算、比較及數學函數。

### 用法
在 JavaScript 中，可以直接使用數字進行運算或作為變量賦值。數字可以是整數或浮點數，並且可以使用數字對象提供的多種方法來進行操作。

### 詳細資訊
1. **數字範圍**：JavaScript 的數字類型可以表示的數值範圍為 `-(2^53 - 1)` 到 `2^53 - 1` 的整數和可表示的浮點數。
2. **特殊數字**：
   - `NaN` (Not-a-Number)：表示非數字值，通常用於數學運算失敗的情況。
   - `Infinity` 和 `-Infinity`：表示正無限大和負無限大。
3. **數字轉換**：可以使用 `Number()` 函數將其他數據類型轉換為數字，或者使用 `parseInt()` 和 `parseFloat()` 函數進行特定的格式轉換。

## 範例
```javascript
// 整數
let a = 10;
let b = 5;

// 浮點數
let c = 10.5;
let d = 2.3;

// 基本運算
console.log(a + b); // 15
console.log(c - d); // 8.2
console.log(a * b); // 50
console.log(a / b); // 2

// 數字轉換
let numStr = "123";
let num = Number(numStr); // 123
console.log(num); // 123
```

## 解釋
- **常見陷阱**：在 JavaScript 中進行數學運算時，可能會遇到浮點數精度問題。例如，`0.1 + 0.2 !== 0.3`，這是因為浮點數在計算機中以二進制表示時的精度限制。
- **數字與字符串的比較**：在比較數字與字符串時，JavaScript 可能會自動進行類型轉換，這可能導致意想不到的結果。
- **使用 `NaN`**：任何與 `NaN` 進行的運算結果都是 `NaN`，並且 `NaN` 與任何數字不相等，包括它自己。

## 簡單總結
JavaScript 中的數字類型是基於 IEEE 754 標準的雙精度浮點數，支持各種數學運算及數據轉換。