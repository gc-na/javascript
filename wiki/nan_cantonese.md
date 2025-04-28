<!--
Meta Description: # JavaScript 中的 NaN：理解非數字型 (Not-a-Number) ## 概述 在 JavaScript 中，`NaN`（Not-a-Number）是一個特殊的數值，表示無法進行的數學運算或解析。它常用於表示數值計算的錯誤情況。 ## 文檔 ### 目的 `NaN` 的主要目的是標識...
Meta Keywords: nan, number, isnan, javascript, parseint
-->

# JavaScript 中的 NaN：理解非數字型 (Not-a-Number)

## 概述
在 JavaScript 中，`NaN`（Not-a-Number）是一個特殊的數值，表示無法進行的數學運算或解析。它常用於表示數值計算的錯誤情況。

## 文檔
### 目的
`NaN` 的主要目的是標識數字運算或類型轉換的失敗。在 JavaScript 中，`NaN` 是一個全局屬性，屬於 `Number` 類別，並且其值為 `NaN`。

### 使用方法
`NaN` 可以出現在以下情況中：
- 嘗試將非數字字符串轉換為數字時，例如 `parseInt("abc")` 會返回 `NaN`。
- 將數字運算中的操作數之一設為 `NaN`，結果亦為 `NaN`，例如 `0 / 0` 和 `Math.sqrt(-1)`。

### 詳細資訊
- `NaN` 是一個數字類型，但是其與任何值進行比較時，包括它自己，結果都是 `false`。因此，檢查 `NaN` 的常用方法是使用 `Number.isNaN()` 或 `isNaN()` 函數。
- `NaN` 的類型是 `number`，但它的特性使其在數值運算中經常出現問題。

## 例子
```javascript
// 例子 1：使用 parseInt 解析非數字字符串
let result1 = parseInt("abc"); // result1 將是 NaN

// 例子 2：數學運算中出現 NaN
let result2 = 0 / 0; // result2 將是 NaN

// 例子 3：計算負數的平方根
let result3 = Math.sqrt(-1); // result3 將是 NaN

// 例子 4：檢查 NaN
console.log(Number.isNaN(result1)); // 輸出：true
```

## 解釋
- **常見陷阱**：使用 `==` 或 `===` 來比較 `NaN`，例如 `NaN === NaN` 將返回 `false`。這是因為 `NaN` 被定義為不等於任何值，包括它自己。
- **使用 `isNaN()` 和 `Number.isNaN()`**：`isNaN()` 函數會檢查一個值是否為 `NaN`，但它會在檢查前進行類型轉換。相比之下，`Number.isNaN()` 僅在參數為 `NaN` 時返回 `true`，這使得它更可靠。

## 一句總結
`NaN` 在 JavaScript 中表示無法進行的數學運算，並且需要特殊處理來檢查其存在。