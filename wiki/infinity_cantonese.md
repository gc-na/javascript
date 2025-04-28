<!--
Meta Description: # JavaScript 中的 Infinity：無限的使用與特性 ## 概要 在 JavaScript 中，`Infinity` 是一個特殊的數值，代表無限大。它是全局對象的一部分，並且可以用來表示超出數字範圍的情況。 ## 文檔 `Infinity` 是 JavaScript 中的一個預設常量，...
Meta Keywords: infinity, javascript, console, log, 無限的使用與特性
-->

# JavaScript 中的 Infinity：無限的使用與特性

## 概要
在 JavaScript 中，`Infinity` 是一個特殊的數值，代表無限大。它是全局對象的一部分，並且可以用來表示超出數字範圍的情況。

## 文檔
`Infinity` 是 JavaScript 中的一個預設常量，表示無窮大。當數字超過 JavaScript 所能表示的最大數值時，這個值會被視為 `Infinity`。此外，`Infinity` 也可以用來進行數學運算，並且在邏輯判斷中可以作為一個特殊的數值。

### 使用方式
- `Infinity` 是一個內置的全局屬性，可以直接使用，而無需任何特殊的導入或聲明。
- 語法範例：
  ```javascript
  console.log(Infinity); // 輸出：Infinity
  ```

### 特性
- `Infinity` 是一個數字類型的值。
- `-Infinity` 代表無窮小，亦是 JavaScript 的一部分。
- 使用 `Infinity` 進行計算時，任何正數加上 `Infinity` 都會得到 `Infinity`，而任何負數加上 `Infinity` 都仍然是 `Infinity`。

## 範例
### 基本使用例子
1. **直接輸出 Infinity**
   ```javascript
   console.log(Infinity); // 輸出：Infinity
   ```

2. **與數字運算**
   ```javascript
   console.log(5 + Infinity); // 輸出：Infinity
   console.log(-5 + Infinity); // 輸出：Infinity
   console.log(Infinity - 10); // 輸出：Infinity
   ```

3. **與比較運算**
   ```javascript
   console.log(100 > Infinity); // 輸出：false
   console.log(Infinity > 1000); // 輸出：true
   ```

## 解釋
在使用 `Infinity` 時，開發者需注意以下幾點：
- `Infinity` 並不是一個數字的實際值，而是一個表示無窮大的符號，這意味著在數學運算中，使用 `Infinity` 的結果可能會導致意想不到的行為。
- 比較運算中，`Infinity` 始終大於任何有限數字。
- 由於 `Infinity` 是一個數字類型，其類型為 `number`，可以用來進行數學運算，但在某些情況下，會造成運算結果不如預期。

## 一句總結
在 JavaScript 中，`Infinity` 是一個表示無限大的特殊常量，廣泛應用於數學運算和邏輯比較中。