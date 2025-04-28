<!--
Meta Description: # 在 JavaScript 中使用 isFinite 函數的完整指南 ## 概要 `isFinite` 是一個 JavaScript 函數，用於檢查一個數值是否為有限數字。該函數返回一個布林值，指示給定的參數是否為有限的數值（不是無窮大或 NaN）。 ## 文檔 ### 目的 `isFinite`...
Meta Keywords: isfinite, console, log, nan, false
-->

# 在 JavaScript 中使用 isFinite 函數的完整指南

## 概要
`isFinite` 是一個 JavaScript 函數，用於檢查一個數值是否為有限數字。該函數返回一個布林值，指示給定的參數是否為有限的數值（不是無窮大或 NaN）。

## 文檔
### 目的
`isFinite` 函數的主要目的是判斷一個數值是否可以被視為有限的，即不會是正無窮大、負無窮大或非數值（NaN）。

### 用法
`isFinite` 函數的語法如下：
```javascript
isFinite(value)
```
- `value`: 需要檢查的數值或表達式。

### 詳細信息
- 如果 `value` 為 `NaN`、`Infinity` 或 `-Infinity`，則返回 `false`。
- 對於所有其他數值，返回 `true`。
- `isFinite` 會將非數值類型（例如字串）轉換為數值進行檢查。如果轉換後的值為有限數字，則返回 `true`。

## 範例
以下是 `isFinite` 的基本用法示例：

### 範例 1：檢查數字
```javascript
console.log(isFinite(10)); // true
console.log(isFinite(-5)); // true
console.log(isFinite(Infinity)); // false
console.log(isFinite(NaN)); // false
```

### 範例 2：檢查字串
```javascript
console.log(isFinite("20")); // true，字串 "20" 被轉換為數字
console.log(isFinite("hello")); // false，字串無法轉換為數字
```

### 範例 3：檢查計算結果
```javascript
console.log(isFinite(100 / 0)); // false，因為結果是 Infinity
console.log(isFinite(0 / 0)); // false，因為結果是 NaN
```

## 解釋
使用 `isFinite` 時有幾個常見的陷阱和注意事項：
1. **類型轉換**：`isFinite` 會自動將非數值類型轉換為數值。如果傳入的是一個字串，且該字串能被轉換為數字，則可能會返回 `true`，這可能會導致意想不到的結果。
2. **NaN 和 Infinity**：確保理解 `NaN` 和 `Infinity` 的行為。這兩者是 `isFinite` 返回 `false` 的原因。
3. **全局作用域**：在全局作用域中，`isFinite` 可能會與其他命名相同的變數產生衝突，建議在使用時明確調用 `window.isFinite()` 以避免問題。

## 一句總結
`isFinite` 函數用於檢查一個數值是否為有限數字，並返回布林值以指示結果。