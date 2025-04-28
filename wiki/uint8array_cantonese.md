<!--
Meta Description: # Uint8Array：JavaScript 中的 8 位無符號整數數組 ## 概述 `Uint8Array` 是 JavaScript 的一個內建類別，用於表示和操作 8 位無符號整數的數組。這種數組特別適合處理二進制數據，如圖像、音頻和其他媒體文件。 ## 文檔 `Uint8Array` 是一...
Meta Keywords: uint8array, javascript, const, arr, new
-->

# Uint8Array：JavaScript 中的 8 位無符號整數數組

## 概述
`Uint8Array` 是 JavaScript 的一個內建類別，用於表示和操作 8 位無符號整數的數組。這種數組特別適合處理二進制數據，如圖像、音頻和其他媒體文件。

## 文檔
`Uint8Array` 是一種類型化數組，提供了一個高效的方式來存儲和操作無符號的整數數據。每個元素的範圍是從 0 到 255。這個類別通常用於 Web 開發中的數據處理，尤其是在使用 Web API（如 WebSockets 和 Fetch API）時。

### 用法
要創建一個 `Uint8Array`，可以使用以下幾種方法：

1. **通過長度創建**：
   ```javascript
   const arr = new Uint8Array(10); // 創建一個長度為10的 Uint8Array，默認值為0
   ```

2. **通過數組創建**：
   ```javascript
   const arr = new Uint8Array([10, 20, 30]); // 創建一個包含指定值的 Uint8Array
   ```

3. **通過類型化數組創建**：
   ```javascript
   const typedArray = new Uint8Array([1, 2, 3]);
   const arr = new Uint8Array(typedArray); // 從另一個 Uint8Array 創建
   ```

### 詳細信息
- **屬性**：
  - `length`：返回數組的長度。
  
- **方法**：
  - `set(array)`: 把傳入的數組元素設置到 `Uint8Array` 中。
  - `subarray(begin, end)`: 返回一個新的 `Uint8Array`，它的元素是原數組的一部分。

## 範例
以下是 `Uint8Array` 的基本用法範例：

### 創建和訪問
```javascript
const arr = new Uint8Array(5); // 創建一個長度為5的 Uint8Array
arr[0] = 10;
arr[1] = 255;
console.log(arr); // 輸出: Uint8Array(5) [10, 255, 0, 0, 0]
```

### 使用 set 方法
```javascript
const arr1 = new Uint8Array(5);
const arr2 = new Uint8Array([1, 2, 3]);
arr1.set(arr2);
console.log(arr1); // 輸出: Uint8Array(5) [1, 2, 3, 0, 0]
```

### 使用 subarray 方法
```javascript
const arr = new Uint8Array([10, 20, 30, 40, 50]);
const subArr = arr.subarray(1, 4);
console.log(subArr); // 輸出: Uint8Array(3) [20, 30, 40]
```

## 解釋
在使用 `Uint8Array` 時，開發者應該注意以下幾點：

- **範圍限制**：`Uint8Array` 中的每個元素必須在 0 到 255 之間，超出這個範圍會自動進行截斷。
- **性能考量**：由於 `Uint8Array` 是類型化數組，它比普通的 JavaScript 數組在處理大量數據時更加高效。
- **二進制數據**：`Uint8Array` 非常適合用於處理二進制數據，例如圖片或音頻數據的處理。

## 一句總結
`Uint8Array` 是一種高效的 JavaScript 類型化數組，用於存儲和操作 8 位無符號整數，特別適合處理二進制數據。