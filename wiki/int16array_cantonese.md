<!--
Meta Description: # Int16Array：JavaScript 中的整數 16 位元數組 ## 簡介 `Int16Array` 是 JavaScript 中一種用於處理 16 位元整數的類別，屬於 Typed Arrays 的一部分，提供了一種有效率的方式來存儲和操作二進制數據。 ## 文檔 ### 目的 `Int...
Meta Keywords: int16array, javascript, let, new, arraybuffer
-->

# Int16Array：JavaScript 中的整數 16 位元數組

## 簡介
`Int16Array` 是 JavaScript 中一種用於處理 16 位元整數的類別，屬於 Typed Arrays 的一部分，提供了一種有效率的方式來存儲和操作二進制數據。

## 文檔
### 目的
`Int16Array` 旨在提供一種高效的方法來處理整數數據，特別是在需要直接操作二進制數據的情況下，例如音頻處理、圖像處理或 WebGL。

### 用法
要創建一個 `Int16Array`，可以使用以下語法：

```javascript
let array = new Int16Array(length);
```
- `length`：指定數組的長度。

你也可以從已有的數組或類似數組的對象創建 `Int16Array`：

```javascript
let arrayFromArray = new Int16Array([1, 2, 3]);
```

此外，`Int16Array` 也可以從一個 ArrayBuffer 創建：

```javascript
let buffer = new ArrayBuffer(16);
let int16Array = new Int16Array(buffer);
```

### 詳細
`Int16Array` 支持多種方法來操作數據，如 `.set()`, `.subarray()`, 以及常見的數組方法，例如 `.map()`, `.forEach()` 等。每個元素的範圍是 -32768 到 32767。

## 範例
### 創建和初始化 Int16Array
```javascript
// 創建一個長度為 5 的 Int16Array
let int16Array = new Int16Array(5);
console.log(int16Array); // 輸出：Int16Array(5) [0, 0, 0, 0, 0]

// 用數據初始化 Int16Array
let initializedArray = new Int16Array([10, 20, 30]);
console.log(initializedArray); // 輸出：Int16Array(3) [10, 20, 30]
```

### 使用 ArrayBuffer
```javascript
let buffer = new ArrayBuffer(8);
let int16Array = new Int16Array(buffer);

// 設置數據
int16Array[0] = 1000;
int16Array[1] = 2000;

console.log(int16Array); // 輸出：Int16Array(4) [1000, 2000]
```

## 解釋
使用 `Int16Array` 時，有一些常見的陷阱需要避免：
- **數據範圍**：確保您存儲的數值在 -32768 到 32767 之間，超出範圍的數據會被截斷。
- **記憶體管理**：由於 `Int16Array` 使用 ArrayBuffer 進行內部存儲，確保在使用完後適時釋放資源。
- **類型轉換**：在將其他數據類型轉換為 `Int16Array` 時，確保數據類型的兼容性。

## 一行總結
`Int16Array` 是一種用於在 JavaScript 中高效處理 16 位元整數的數組類別。