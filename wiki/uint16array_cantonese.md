<!--
Meta Description: # Uint16Array：JavaScript 中的 16 位無符號整數數組 ## 簡介 `Uint16Array` 是 JavaScript 中的一種類型化數組，用於儲存 16 位無符號整數。它允許開發者以高效的方式處理二進制數據，特別是在需要與 Web API 和其他底層操作相互作用時。 ##...
Meta Keywords: uint16array, javascript, let, new, arr
-->

# Uint16Array：JavaScript 中的 16 位無符號整數數組

## 簡介
`Uint16Array` 是 JavaScript 中的一種類型化數組，用於儲存 16 位無符號整數。它允許開發者以高效的方式處理二進制數據，特別是在需要與 Web API 和其他底層操作相互作用時。

## 文件說明
`Uint16Array` 主要用於處理需要精確數據儲存的情境，比如圖形處理、音頻數據處理、或是網絡數據的傳輸。這種數組的每個元素都佔用 2 個字節，能夠儲存從 0 到 65535 的整數。

### 目的
- 儲存和處理 16 位無符號整數數據。
- 提供高效的內存使用和快速的計算性能。

### 用法
要創建 `Uint16Array`，可以使用以下幾種方法：
1. **通過數組長度創建**：
   ```javascript
   let arr = new Uint16Array(5);
   ```

2. **通過數組實例創建**：
   ```javascript
   let arr = new Uint16Array([1, 2, 3, 4, 5]);
   ```

3. **通過另一個類型化數組或常規數組創建**：
   ```javascript
   let typedArray = new Uint8Array([255, 128, 64]);
   let arr = new Uint16Array(typedArray);
   ```

4. **通過 ArrayBuffer 創建**：
   ```javascript
   let buffer = new ArrayBuffer(10);
   let arr = new Uint16Array(buffer);
   ```

## 範例
### 基本用法範例
```javascript
// 創建一個 Uint16Array
let myArray = new Uint16Array(3);
myArray[0] = 1000;
myArray[1] = 2000;
myArray[2] = 3000;

console.log(myArray); // 輸出: Uint16Array(3) [1000, 2000, 3000]
```

### 使用 ArrayBuffer
```javascript
let buffer = new ArrayBuffer(6); // 6 bytes
let uint16View = new Uint16Array(buffer);

uint16View[0] = 32000;
uint16View[1] = 65000;

console.log(uint16View); // 輸出: Uint16Array(3) [32000, 65000]
```

## 解釋
### 常見問題
- **超出範圍的數值**：若嘗試把超出 0 到 65535 範圍的數值賦值給 `Uint16Array`，會自動將其轉換為有效的範圍內的數值。例如：
  ```javascript
  let arr = new Uint16Array(1);
  arr[0] = 70000; // 70000 會被轉換為 4464
  console.log(arr[0]); // 輸出: 4464
  ```

- **性能考量**：使用類型化數組可以提高性能，尤其在處理大量數據時，因為它們使用固定大小的數據類型並在內存中佔用連續的空間。

## 一句總結
`Uint16Array` 是 JavaScript 的一種類型化數組，專門用於儲存和處理 16 位無符號整數，以提高性能和數據管理的效率。