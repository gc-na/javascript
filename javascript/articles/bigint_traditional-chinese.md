<!--
Meta Description: # BigInt 在 JavaScript 中的應用及特性 ## 概述 BigInt 是 JavaScript 中一種新的原始數據類型，用於表示大於 `2^53 - 1` 或小於 `-(2^53 - 1)` 的整數。這使得開發者能夠處理超出普通 Number 類型範圍的整數，並避免數據溢出問題。 #...
Meta Keywords: bigint, javascript, number, const, bigint1
-->

# BigInt 在 JavaScript 中的應用及特性

## 概述
BigInt 是 JavaScript 中一種新的原始數據類型，用於表示大於 `2^53 - 1` 或小於 `-(2^53 - 1)` 的整數。這使得開發者能夠處理超出普通 Number 類型範圍的整數，並避免數據溢出問題。

## 文檔
### 目的
BigInt 的主要目的是解決 JavaScript 中 Number 類型的整數範圍限制。當需要精確計算大數字或在加密、金融等高精度應用中時，BigInt 顯得特別重要。

### 使用方法
要創建 BigInt，可以使用以下幾種方式：
1. 在數字後面加上 `n`，如 `12345678901234567890n`
2. 使用 `BigInt()` 函數，如 `BigInt(12345678901234567890)`

### 詳細說明
- BigInt 不能與 Number 直接進行運算，必須先轉換或使用相同類型。
- 在進行運算時，結果會自動轉換為 BigInt，如 `1n + 2n` 將返回 `3n`。
- BigInt 不能與非整數進行比較。例如，`BigInt(1) < 2` 會返回 `false`。

## 範例
### 基本用法
```javascript
// 創建 BigInt
const bigInt1 = 12345678901234567890n;
const bigInt2 = BigInt(12345678901234567890);

// 大數相加
const sum = bigInt1 + bigInt2;  // 24691357802469135780n

// 大數相乘
const product = bigInt1 * 2n;    // 24691357802469135780n

// 比較大小
console.log(bigInt1 > bigInt2);   // false
```

## 解釋
在使用 BigInt 時，開發者需要注意以下幾點：
- **運算限制**：BigInt 和 Number 之間不能直接進行運算，這可能導致 TypeError。
- **性能考量**：由於 BigInt 的運算速度比普通 Number 慢，因此在性能敏感的場景中需要謹慎使用。
- **JSON 支持**：BigInt 無法直接用於 JSON 中的序列化和反序列化，這需要額外處理。

## 總結
BigInt 使 JavaScript 能夠處理大整數，避免了數據溢出問題，對於高精度的數據計算非常有用。