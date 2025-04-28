<!--
Meta Description: # Uint8Array：JavaScript 中的 8 位無符號整數數組 ## 摘要 `Uint8Array` 是 JavaScript 中的一種類型化數組，它用於處理 8 位無符號整數的數據。這種數組是二進制數據處理的有效工具，特別適合用於 Web 應用的圖像、音頻及其他媒體數據。 ## 文檔 ...
Meta Keywords: uint8array, javascript, uint8, const, new
-->

# Uint8Array：JavaScript 中的 8 位無符號整數數組

## 摘要
`Uint8Array` 是 JavaScript 中的一種類型化數組，它用於處理 8 位無符號整數的數據。這種數組是二進制數據處理的有效工具，特別適合用於 Web 應用的圖像、音頻及其他媒體數據。

## 文檔
`Uint8Array` 是一種內建的類型化數組，允許開發者以高效的方式存取和操作二進制數據。每個元素的範圍是從 0 到 255，適用於需要精確控制數據的應用場景。

### 目的
`Uint8Array` 的主要目的在於提供一種更低階的數據處理方式，使開發者能夠直接操作原始二進制數據，尤其是在進行網絡請求或處理文件時。

### 用法
可以通過以下幾種方式來創建 `Uint8Array`：

1. **從數組初始化**：
   ```javascript
   const uint8 = new Uint8Array([10, 20, 30]);
   ```

2. **指定長度初始化**：
   ```javascript
   const uint8 = new Uint8Array(3); // 創建長度為3的空數組
   ```

3. **從其他類型的數組複製**：
   ```javascript
   const array = new Array(10, 20, 30);
   const uint8 = new Uint8Array(array);
   ```

4. **從 ArrayBuffer 創建**：
   ```javascript
   const buffer = new ArrayBuffer(3);
   const uint8 = new Uint8Array(buffer);
   ```

### 詳細資訊
- **屬性**：`Uint8Array` 提供了多種屬性，如 `length`，用於返回數組的長度。
- **方法**：常用的方法包括 `set()`, `subarray()`, `slice()`等，這些方法允許開發者進行數據的操作與處理。

## 範例
以下是幾個基本使用範例：

### 創建 Uint8Array
```javascript
const uint8 = new Uint8Array([1, 2, 3, 4, 5]);
console.log(uint8); // 輸出: Uint8Array(5) [1, 2, 3, 4, 5]
```

### 設置數據
```javascript
const uint8 = new Uint8Array(5);
uint8.set([10, 20, 30]); // 設置前三個元素
console.log(uint8); // 輸出: Uint8Array(5) [10, 20, 30, 0, 0]
```

### 數組切片
```javascript
const uint8 = new Uint8Array([5, 10, 15, 20, 25]);
const sliced = uint8.slice(1, 4);
console.log(sliced); // 輸出: Uint8Array(3) [10, 15, 20]
```

## 解釋
在使用 `Uint8Array` 時，開發者需要注意以下幾點：
- **數據範圍**：所有元素必須在 0 到 255 之間，超出範圍的值會被截斷。
- **性能考量**：對於大型數據集的操作，`Uint8Array` 提供了比普通數組更高的性能和效率。
- **相容性**：`Uint8Array` 在大多數現代瀏覽器和 JavaScript 環境中得到支持，但在一些舊版環境中可能不完全相容。

## 總結
`Uint8Array` 是 JavaScript 中一種高效處理 8 位無符號整數數據的工具，對於需要操作二進制數據的應用程式特別實用。