<!--
Meta Description: # BigUint64Array：JavaScript 的大整數數組類型 ## 簡介 `BigUint64Array` 是 JavaScript 中的一種數組類型，專門用來存儲 64 位無符號整數。這種數組類型特別適合需要處理大型整數的應用場景，並且能夠有效地進行數據的存取和操作。 ## 文檔 ##...
Meta Keywords: biguint64array, javascript, bigintarray, let, new
-->

# BigUint64Array：JavaScript 的大整數數組類型

## 簡介
`BigUint64Array` 是 JavaScript 中的一種數組類型，專門用來存儲 64 位無符號整數。這種數組類型特別適合需要處理大型整數的應用場景，並且能夠有效地進行數據的存取和操作。

## 文檔
### 目的
`BigUint64Array` 用於處理和存儲大於 JavaScript 原生數字類型所能表示的整數，特別是在需要進行高精度計算的情況下。這種數組類型的每個元素都是一個 64 位的無符號整數，能夠表示的數字範圍從 0 到 2^64-1。

### 使用方法
要創建一個 `BigUint64Array`，可以使用以下語法：

```javascript
let bigUintArray = new BigUint64Array(length);
```

- `length`：數組的長度，表示要創建的元素個數。

你也可以從一個現有的數組或類似數組的物件創建 `BigUint64Array`：

```javascript
let bigUintArrayFromArray = new BigUint64Array([1n, 2n, 3n]);
```

### 詳細信息
- `BigUint64Array` 只接受 BigInt 類型的數字（即以 `n` 結尾的整數）。
- 每個元素都佔用 8 個字節。
- 支援常用的數組方法，如 `.set()`, `.subarray()`, 和 `.slice()`。

## 示例
以下是如何使用 `BigUint64Array` 的基本範例：

```javascript
// 創建一個長度為 3 的 BigUint64Array
let bigIntArray = new BigUint64Array(3);

// 設置數值
bigIntArray[0] = 9007199254740991n; // 設置第一個元素
bigIntArray[1] = 18446744073709551615n; // 設置第二個元素
bigIntArray[2] = 12345678901234567890n; // 設置第三個元素

// 輸出數組
console.log(bigIntArray); // BigUint64Array(3) [ 9007199254740991n, 18446744073709551615n, 12345678901234567890n ]

// 使用 set 方法
let anotherArray = new BigUint64Array([5n, 10n]);
bigIntArray.set(anotherArray, 0);
console.log(bigIntArray); // BigUint64Array(3) [ 5n, 10n, 12345678901234567890n ]
```

## 解釋
在使用 `BigUint64Array` 時，有幾個常見的陷阱和注意事項：
- 確保所有數值都是 BigInt 類型，否則會拋出錯誤。
- 不要嘗試將普通數字（Number）直接賦值給 `BigUint64Array`，必須將其轉換為 BigInt。
- 這個類型不支持負數，因為它僅限於無符號整數。

## 一句總結
`BigUint64Array` 是一個用於存儲和操作 64 位無符號整數的數組類型，適用於需要高精度計算的 JavaScript 應用。