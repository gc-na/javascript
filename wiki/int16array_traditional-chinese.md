<!--
Meta Description: # Int16Array：JavaScript 中的 16 位整數陣列 ## 概要 `Int16Array` 是 JavaScript 中的一種類型化陣列，專門用來處理 16 位帶符號整數。它允許開發人員在處理二進位數據時高效地存儲和操作整數數組。 ## 文檔 `Int16Array` 是 ECMA...
Meta Keywords: int16array, javascript, let, int16, new
-->

# Int16Array：JavaScript 中的 16 位整數陣列

## 概要
`Int16Array` 是 JavaScript 中的一種類型化陣列，專門用來處理 16 位帶符號整數。它允許開發人員在處理二進位數據時高效地存儲和操作整數數組。

## 文檔
`Int16Array` 是 ECMAScript 6（ES6）引入的 TypedArray 的一部分。它提供了一個可變長度的陣列，專門用來存儲範圍從 -32768 到 32767 的整數。這對於需要高效內存使用的應用程序（如音訊處理、影像處理或數據通信）特別有用。

### 使用方法
要創建一個 `Int16Array`，可以使用以下語法：

```javascript
let array = new Int16Array(length);
```

這裡的 `length` 是你希望創建的陣列的長度。你也可以直接從一個已存在的數組或陣列視圖創建 `Int16Array`：

```javascript
let arrayFromArray = new Int16Array([1, 2, 3, 4]);
```

### 屬性和方法
- **length**: 返回陣列的長度。
- **set(array)**: 將一個數組或 TypedArray 的值複製到 `Int16Array` 中。
- **subarray(begin, end)**: 返回一個新的 `Int16Array`，它是從原始陣列的一部分。

## 範例
以下是一些基本的 `Int16Array` 用法示例：

### 創建 Int16Array
```javascript
let int16 = new Int16Array(5);
console.log(int16); // Int16Array(5) [0, 0, 0, 0, 0]
```

### 使用數組初始化
```javascript
let int16FromArray = new Int16Array([32767, -32768, 0]);
console.log(int16FromArray); // Int16Array(3) [32767, -32768, 0]
```

### 設置值
```javascript
let int16 = new Int16Array(3);
int16.set([100, 200, 300]);
console.log(int16); // Int16Array(3) [100, 200, 44]
```

### 使用 subarray 方法
```javascript
let int16 = new Int16Array([10, 20, 30, 40]);
let subArray = int16.subarray(1, 3);
console.log(subArray); // Int16Array(2) [20, 30]
```

## 解釋
在使用 `Int16Array` 時，有幾個常見的注意事項：
- **範圍限制**: `Int16Array` 僅能存儲 -32768 到 32767 的整數，超出範圍的數值會被截斷或轉換。
- **性能考量**: 在需要大量數據運算的情況下，使用類型化陣列可以提高性能，因為它們在內存中是連續的，並且能有效利用緩存。
- **與其他類型的兼容性**: 將 `Int16Array` 與其他類型的數組或陣列視圖一起使用時，需小心數據類型轉換。

## 總結
`Int16Array` 是一種專為 16 位整數設計的高效類型化陣列，適合需要處理大量二進位數據的應用。