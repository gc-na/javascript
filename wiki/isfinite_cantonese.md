<!--
Meta Description: # JavaScript 中的 isFinite 函數：確定數字是否為有限數值 ## 簡介 `isFinite` 是 JavaScript 的一個內建函數，用於檢查一個數值是否為有限值。這對於數據驗證和計算中的錯誤處理非常重要。 ## 文檔 `isFinite` 函數的主要目的是檢查一個數字是否是有...
Meta Keywords: isfinite, true, false, console, log
-->

# JavaScript 中的 isFinite 函數：確定數字是否為有限數值

## 簡介
`isFinite` 是 JavaScript 的一個內建函數，用於檢查一個數值是否為有限值。這對於數據驗證和計算中的錯誤處理非常重要。

## 文檔
`isFinite` 函數的主要目的是檢查一個數字是否是有限的。有限數字是指不是 `Infinity`、`-Infinity` 或 `NaN` 的數字。

### 語法
```javascript
isFinite(value)
```

### 參數
- **value**: 要檢查的值，可以是任何類型。

### 返回值
- 返回 `true` 如果 `value` 是一個有限數字，否則返回 `false`。

### 用法
`isFinite` 通常用於數據驗證中的檢查，確保數值在計算或顯示之前是有效的。

## 範例
以下是一些使用 `isFinite` 的基本範例：

```javascript
console.log(isFinite(10));          // 返回 true
console.log(isFinite(Infinity));     // 返回 false
console.log(isFinite(-Infinity));    // 返回 false
console.log(isFinite(NaN));          // 返回 false
console.log(isFinite("123"));        // 返回 true，會轉換為數字
console.log(isFinite("Hello"));      // 返回 false，因為不是數字
```

## 解釋
- **常見陷阱**: 使用 `isFinite` 檢查字符串時，若字符串能轉換為數字，則會返回 `true`。例如，`isFinite("123")` 會返回 `true`，但 `isFinite("Hello")` 會返回 `false`。
- **數據類型**: `isFinite` 會自動將非數字類型轉換為數字來進行檢查，因此在使用時要注意數據類型的影響。
- **邊界案例**: 當傳遞 `undefined` 或 `null` 時，這些值會被轉換為 `0`，因此 `isFinite(undefined)` 和 `isFinite(null)` 都會返回 `true`。

## 總結
`isFinite` 是一個簡單而強大的工具，用於確定一個值是否為有效的有限數字。