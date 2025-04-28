<!--
Meta Description: # JavaScript 中的 isNaN 函數：判斷值是否為非數字 ## 概述 `isNaN` 是 JavaScript 中的一個全局函數，用來判斷一個值是否是 `NaN`（非數字）。在進行數字運算時，確保數據的有效性和類型是非常重要的，`isNaN` 函數能幫助開發者檢查變量的狀態。 ## 文檔...
Meta Keywords: isnan, nan, true, false, console
-->

# JavaScript 中的 isNaN 函數：判斷值是否為非數字

## 概述
`isNaN` 是 JavaScript 中的一個全局函數，用來判斷一個值是否是 `NaN`（非數字）。在進行數字運算時，確保數據的有效性和類型是非常重要的，`isNaN` 函數能幫助開發者檢查變量的狀態。

## 文檔
### 目的
`isNaN` 函數的主要目的是判斷傳入的參數是否是 `NaN`。`NaN` 是一個特殊的數值，表示一個無效的數字計算結果，比如零除以零。

### 使用方法
`isNaN` 函數的語法如下：
```javascript
isNaN(value)
```
- `value`：需要進行檢查的值。可以是任何類型的數據。

返回值：
- 如果 `value` 是 `NaN` 或無法轉換為數字，則返回 `true`；否則返回 `false`。

### 詳細說明
- `isNaN` 在內部使用 `Number` 函數將傳入的值轉換為數字，然後檢查該結果是否為 `NaN`。
- `NaN` 本身與任何值都不相等，包括它自己，這是 `NaN` 的一個重要特徵。
- 使用 `isNaN` 時，需注意它在某些情況下可能會返回 `true`，例如對於空字串和非數字字符串。

## 範例
### 基本用法
以下是一些 `isNaN` 函數的基本使用範例：

```javascript
console.log(isNaN(NaN));        // true
console.log(isNaN(123));        // false
console.log(isNaN("123"));      // false (因為可以轉換成數字)
console.log(isNaN("Hello"));    // true (因為不能轉換成數字)
console.log(isNaN(undefined));   // true
console.log(isNaN(null));       // false (null 會被轉換為 0)
```

## 解釋
### 常見陷阱
- **類型轉換**：`isNaN` 會將傳入的值進行類型轉換，這可能導致一些意外的結果。例如，空字串 `""` 和 `null` 都會返回 `false`，因為它們被轉換為 0。
- **全局 `isNaN` 與 `Number.isNaN`**：全局 `isNaN` 會進行類型轉換，而 `Number.isNaN` 只會檢查值是否為 `NaN`。這意味著 `Number.isNaN("Hello")` 將返回 `false`，而 `isNaN("Hello")` 會返回 `true`。

### 附加說明
為了更精確地檢查非數字值，建議使用 `Number.isNaN`，這樣可以避免意外的類型轉換。

## 總結
`isNaN` 是一個用於判斷值是否為非數字的有效工具，能幫助開發者確認數據的有效性。