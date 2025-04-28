<!--
Meta Description: # Uint16Array：JavaScript 中的無符號 16 位整數陣列 ## 簡介 `Uint16Array` 是 JavaScript 提供的一種類型化陣列，專門用於儲存無符號的 16 位整數。它使得在處理二進制數據時更加高效，特別是在需要操作大量數字的情況下。 ## 文檔 ### 目的 ...
Meta Keywords: uint16array, arr, javascript, let, new
-->

# Uint16Array：JavaScript 中的無符號 16 位整數陣列

## 簡介
`Uint16Array` 是 JavaScript 提供的一種類型化陣列，專門用於儲存無符號的 16 位整數。它使得在處理二進制數據時更加高效，特別是在需要操作大量數字的情況下。

## 文檔
### 目的
`Uint16Array` 允許開發者創建一個由無符號 16 位整數組成的陣列，這些整數的範圍是從 0 到 65535。這在處理圖形數據、音頻數據或其他需要高效存儲的情況下非常有用。

### 使用方式
可以通過以下方式創建 `Uint16Array`：
1. **不帶參數**：創建一個指定長度的空 `Uint16Array`。
   ```javascript
   let arr = new Uint16Array(5); // 創建一個長度為 5 的 Uint16Array
   ```
   
2. **使用陣列或類似陣列的物件**：將現有的數值轉換為 `Uint16Array`。
   ```javascript
   let arr = new Uint16Array([1, 2, 3, 65535]); // 使用數組初始化
   ```

3. **使用另一個類型化陣列**：可以將其他類型化陣列轉換為 `Uint16Array`。
   ```javascript
   let uint8 = new Uint8Array([1, 2, 3, 4]);
   let arr = new Uint16Array(uint8); // 從 Uint8Array 創建 Uint16Array
   ```

### 詳細資訊
- `Uint16Array` 支援各種操作，例如 `set()`、`subarray()` 和 `slice()` 等方法。
- 陣列的索引從 0 開始，並且可以使用 `length` 屬性獲取陣列的長度。
- 像所有類型化陣列一樣，`Uint16Array` 的元素會在訪問時自動轉換為無符號 16 位整數。

## 範例
### 基本用法
```javascript
// 創建一個 Uint16Array
let arr = new Uint16Array(3);
arr[0] = 1000;
arr[1] = 30000;
arr[2] = 50000;

console.log(arr); // 輸出: Uint16Array(3) [ 1000, 30000, 50000 ]
```

### 使用 set 方法
```javascript
let arr = new Uint16Array(3);
arr.set([2000, 4000]); // 將 2000 和 4000 設置到陣列中

console.log(arr); // 輸出: Uint16Array(3) [ 2000, 4000, 0 ]
```

### 使用 subarray 方法
```javascript
let arr = new Uint16Array([10, 20, 30, 40]);
let subArr = arr.subarray(1, 3); // 獲取子陣列

console.log(subArr); // 輸出: Uint16Array(2) [ 20, 30 ]
```

## 解釋
### 常見問題
- **數據溢出**：當試圖將超出 0-65535 範圍的數字賦值給 `Uint16Array` 時，會自動進行模 65536 的運算。例如：
  ```javascript
  let arr = new Uint16Array(1);
  arr[0] = 70000; 
  console.log(arr[0]); // 輸出: 4464
  ```
  
- **類型轉換**：當將非數字類型賦值給 `Uint16Array` 時，會自動進行類型轉換，可能會導致意外行為。

## 單行總結
`Uint16Array` 是一種高效的 JavaScript 類型化陣列，專門用於儲存無符號的 16 位整數，適用於處理大量數據的情境。