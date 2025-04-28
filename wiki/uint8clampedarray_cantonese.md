<!--
Meta Description: # Uint8ClampedArray：JavaScript 中的無符號 8 位元緊湊陣列 ## 概述 `Uint8ClampedArray` 是 JavaScript 中的一種數據結構，用於表示整數數組，每個整數範圍從 0 到 255。這種陣列在處理圖像數據或其他需要限制數值範圍的應用中非常有用。...
Meta Keywords: uint8clampedarray, javascript, 255, const, new
-->

# Uint8ClampedArray：JavaScript 中的無符號 8 位元緊湊陣列

## 概述
`Uint8ClampedArray` 是 JavaScript 中的一種數據結構，用於表示整數數組，每個整數範圍從 0 到 255。這種陣列在處理圖像數據或其他需要限制數值範圍的應用中非常有用。

## 文檔
`Uint8ClampedArray` 是 `TypedArray` 的一種，專門設計用來存儲無符號 8 位元整數。當向 `Uint8ClampedArray` 中寫入值時，如果數值超出範圍（小於 0 或大於 255），則會自動進行修正：小於 0 的值將變為 0，大於 255 的值將變為 255。

### 用法
1. **創建 Uint8ClampedArray**
   ```javascript
   const arr = new Uint8ClampedArray(length);
   ```
   這將創建一個指定長度的 `Uint8ClampedArray`，所有元素初始為 0。

2. **用數組初始化**
   ```javascript
   const arr = new Uint8ClampedArray([256, -5, 100, 300]);
   ```
   在這個例子中，`arr` 會包含 `[255, 0, 100, 255]`，因為數據會被修正到有效範圍內。

3. **數組方法**
   `Uint8ClampedArray` 支持數組的多種方法，如 `map()`, `forEach()`, `reduce()` 等。

## 範例
以下是一些基本的用法範例：

### 創建一個空的 Uint8ClampedArray
```javascript
const emptyArray = new Uint8ClampedArray(5);
console.log(emptyArray); // 輸出: Uint8ClampedArray(5) [0, 0, 0, 0, 0]
```

### 用數組來初始化
```javascript
const clampedArray = new Uint8ClampedArray([10, 260, -20, 128]);
console.log(clampedArray); // 輸出: Uint8ClampedArray(4) [10, 255, 0, 128]
```

### 使用方法
```javascript
const originalArray = new Uint8ClampedArray([10, 20, 30]);
const newArray = originalArray.map(x => x * 2);
console.log(newArray); // 輸出: Uint8ClampedArray(3) [20, 40, 60]
```

## 解釋
在使用 `Uint8ClampedArray` 時，開發者需注意以下幾點：
- 自動修正：如前所述，任何超出範圍的數值都會被修正，這可能導致意外的結果。
- 性能：`TypedArray` 在處理大量數據時的性能優於普通數組，但對於小數據集，性能差異不明顯。
- 不支持某些數組方法：某些常用的數組方法（如 `splice`）在 `Uint8ClampedArray` 上不可用。

## 一句話總結
`Uint8ClampedArray` 是一個專為存儲無符號 8 位元整數而設計的 JavaScript 陣列，並自動將超出範圍的值修正至 0 或 255。