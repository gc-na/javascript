<!--
Meta Description: # JavaScript 中的 Infinity：無窮大常數的完整指南 ## 摘要 在 JavaScript 中，`Infinity` 是一個特殊的數值，表示數學上的無窮大。它是數學運算的一部分，並且在數據處理和計算中具有廣泛的應用。 ## 文檔 `Infinity` 是一個全局屬性，表示一個超過所...
Meta Keywords: infinity, javascript, console, log, true
-->

# JavaScript 中的 Infinity：無窮大常數的完整指南

## 摘要
在 JavaScript 中，`Infinity` 是一個特殊的數值，表示數學上的無窮大。它是數學運算的一部分，並且在數據處理和計算中具有廣泛的應用。

## 文檔
`Infinity` 是一個全局屬性，表示一個超過所有數字的數值。它在數學運算中自動生成，例如當一個數字被零除時，JavaScript 將返回 `Infinity`。同時，`Infinity` 的數值類型為 `number`。

### 目的
`Infinity` 的主要用途是在數學計算中進行範圍檢查或判斷某個數是否超過了可表示的最大值。這使得在處理數據時能夠更靈活地管理極端情況。

### 使用方法
在 JavaScript 中，`Infinity` 可以直接使用，而不需要任何額外的操作。用法示例如下：
```javascript
console.log(Infinity); // 輸出：Infinity
```

## 範例
以下是一些 `Infinity` 的基本使用範例：

1. **數學運算**：
   ```javascript
   console.log(1 / 0); // 輸出：Infinity
   ```

2. **比較**：
   ```javascript
   console.log(Infinity > 1000); // 輸出：true
   console.log(Infinity === Infinity); // 輸出：true
   ```

3. **與其他數值的運算**：
   ```javascript
   console.log(Infinity + 100); // 輸出：Infinity
   console.log(Infinity - Infinity); // 輸出：NaN
   ```

## 解釋
使用 `Infinity` 時，開發者需要注意幾個常見的錯誤和陷阱：
- **與零的運算**：將任意數字除以零的結果為 `Infinity`，但如果將 `Infinity` 減去 `Infinity`，則結果為 `NaN`（非數字），這可能會導致意外行為。
- **類型檢查**：雖然 `Infinity` 是一個數字類型，但在某些情況下進行比較或運算時，可能會有意外結果，例如與 `null` 或 `undefined` 的比較。

## 一行總結
在 JavaScript 中，`Infinity` 表示無窮大的數值，用於數學運算和極端數據處理。