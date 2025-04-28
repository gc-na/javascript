<!--
Meta Description: # JavaScript 中的 isNaN 函數：檢查數據是否為 NaN ## 概述 `isNaN` 是 JavaScript 中的一個全局函數，用於檢查一個值是否為 `NaN`（Not-a-Number）。這個函數在數據類型轉換和數據驗證中非常有用。 ## 文檔 ### 目的 `isNaN` 函數...
Meta Keywords: isnan, nan, true, console, log
-->

# JavaScript 中的 isNaN 函數：檢查數據是否為 NaN

## 概述
`isNaN` 是 JavaScript 中的一個全局函數，用於檢查一個值是否為 `NaN`（Not-a-Number）。這個函數在數據類型轉換和數據驗證中非常有用。

## 文檔
### 目的
`isNaN` 函數的主要目的是判斷一個值是否為 `NaN`。`NaN` 是一個特殊的數值，表示非數字的數據，常出現在數學計算或類型轉換中。

### 使用方法
```javascript
isNaN(value);
```
- **參數**: `value` - 需要檢查的值，可以是任何數據類型。
- **返回值**: 如果 `value` 是 `NaN` 或可以轉換為 `NaN`，則返回 `true`；否則返回 `false`。

### 詳細說明
- `NaN` 是 JavaScript 中的一個特殊值，表示一個無法表示的數字。
- `isNaN` 會將傳入的值轉換為數字，然後檢查結果是否為 `NaN`。
- 注意，使用 `isNaN` 檢查 `undefined`、空字符串或非數字字符串等非數字類型時，會先進行隱式類型轉換。

## 示例
### 基本用法
```javascript
console.log(isNaN(NaN));          // true
console.log(isNaN(123));          // false
console.log(isNaN('123'));        // false
console.log(isNaN('Hello'));      // true
console.log(isNaN(undefined));    // true
console.log(isNaN(null));         // false
```

## 解釋
- **常見誤區**: 很多人誤認為 `isNaN` 只檢查數字類型，但其實它會嘗試將所有值轉換為數字。在處理字符串時，這可能會導致意想不到的結果。
- **避免使用**: 對於需要準確檢查數值的情況，建議使用 `Number.isNaN()`，因為它不會對非數字類型進行隱式轉換。
  
### 例外情況
- `isNaN(NaN)` 和 `isNaN('Hello')` 返回 `true`，而 `isNaN(123)` 和 `isNaN('123')` 返回 `false`。
- `isNaN()` 在 ES6 之前的行為可能會讓人困惑，如在某些情況下，它會返回 `true` 甚至對於空字符串。

## 一句總結
`isNaN` 函數用於檢查一個值是否是 `NaN`，並且在隱式類型轉換中表現出特定的行為。