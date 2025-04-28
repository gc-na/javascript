<!--
Meta Description: # Int8Array：JavaScript 中的有符號 8 位元整數陣列 ## 概述 `Int8Array` 是 JavaScript 提供的一種類型化陣列，專門用於儲存有符號的 8 位元整數。它允許開發者以高效的方式處理二進位資料，特別是在需要處理大量數據時，如圖像處理、網絡傳輸等情境。 ## ...
Meta Keywords: int8array, javascript, const, new, arraybuffer
-->

# Int8Array：JavaScript 中的有符號 8 位元整數陣列

## 概述
`Int8Array` 是 JavaScript 提供的一種類型化陣列，專門用於儲存有符號的 8 位元整數。它允許開發者以高效的方式處理二進位資料，特別是在需要處理大量數據時，如圖像處理、網絡傳輸等情境。

## 文件說明
`Int8Array` 是 ECMAScript 2015 (ES6) 中引入的一部分，屬於 JavaScript 的 ArrayBuffer 類型化陣列系列。這種陣列的每個元素都是一個有符號的 8 位元整數，範圍從 -128 到 127。`Int8Array` 的主要用途是在需要進行高效數據處理時，提供一種能夠直接操作二進位資料的方式。

### 用法
要創建一個 `Int8Array`，您可以使用以下方式：
1. 直接傳入長度：
   ```javascript
   const int8 = new Int8Array(10); // 創建一個長度為 10 的 Int8Array
   ```

2. 傳入陣列或其他類型化陣列：
   ```javascript
   const int8 = new Int8Array([10, 20, -30, 127]); // 使用數組初始化
   ```

3. 從 ArrayBuffer 創建：
   ```javascript
   const buffer = new ArrayBuffer(16);
   const int8 = new Int8Array(buffer); // 從 ArrayBuffer 創建 Int8Array
   ```

### 詳細參數
- **長度**：`Int8Array` 的長度可以在創建時指定，這會初始化為 0。
- **元素存取**：可以通過索引來存取和修改元素，範圍是從 0 到 length - 1。
- **方法**：`Int8Array` 支援常用的陣列方法，如 `map`、`filter`、`forEach` 等，但不支援 `push` 或 `pop` 等修改陣列大小的方法。

## 示例
以下是一些基本的使用範例：

1. 創建並初始化 `Int8Array`：
   ```javascript
   const numbers = new Int8Array([1, 2, 3, -4, -5]);
   console.log(numbers); // 輸出：Int8Array(5) [1, 2, 3, -4, -5]
   ```

2. 修改元素：
   ```javascript
   const numbers = new Int8Array(5);
   numbers[0] = 100;
   numbers[1] = -50;
   console.log(numbers); // 輸出：Int8Array(5) [100, -50, 0, 0, 0]
   ```

3. 從 ArrayBuffer 創建：
   ```javascript
   const buffer = new ArrayBuffer(8);
   const int8 = new Int8Array(buffer);
   int8[0] = 64;
   console.log(int8[0]); // 輸出：64
   ```

## 解釋
在使用 `Int8Array` 時，有一些常見的陷阱和注意事項：
- **範圍限制**：`Int8Array` 的值只能在 -128 到 127 之間，超出這一範圍的值會自動進行環繞 (wrapping)。
- **數據類型**：`Int8Array` 是一個類型化陣列，這意味著它只能儲存特定類型的數據，不能直接存入其他數據類型。
- **性能考量**：在處理大量數據時，使用類型化陣列如 `Int8Array` 可以顯著提高性能，因為它們使用更緊湊的記憶體表示。

## 一句總結
`Int8Array` 是 JavaScript 中專門用於存儲有符號 8 位元整數的類型化陣列，提供高效的二進位資料處理能力。