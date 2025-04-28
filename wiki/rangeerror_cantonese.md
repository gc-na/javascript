<!--
Meta Description: # JavaScript 中的 RangeError：詳細指南與示例 ## 概述 RangeError 是一種內建的錯誤類型，在 JavaScript 中用來表示數值超出了可接受的範圍。它通常出現於數學計算或處理數組時，當提供的數值不在預期的範圍內時，就會拋出此錯誤。 ## 文檔 ### 目的 Ra...
Meta Keywords: rangeerror, javascript, slice, console, num
-->

# JavaScript 中的 RangeError：詳細指南與示例

## 概述
RangeError 是一種內建的錯誤類型，在 JavaScript 中用來表示數值超出了可接受的範圍。它通常出現於數學計算或處理數組時，當提供的數值不在預期的範圍內時，就會拋出此錯誤。

## 文檔
### 目的
RangeError 的主要目的是幫助開發者識別和處理數值範圍的問題，從而避免在運行時出現不可預期的行為。這對於確保應用程序的穩定性和可靠性至關重要。

### 使用
當一個函數或方法的參數超出了其定義的範圍時，JavaScript 會自動拋出 RangeError。這通常涉及到數組的索引、數學運算或是其他需要範圍檢查的情況。

### 詳細信息
- **構造函數**: `RangeError` 可以使用 `new RangeError(message)` 來創建一個新的 RangeError 實例，其中 `message` 是一個可選的錯誤描述。
- **拋出時機**: 當調用數組的 `slice()` 方法時，如果提供的起始或結束索引不在有效範圍內，則會拋出 RangeError。

## 示例
### 基本用法
```javascript
// 在數組中使用 slice() 方法
let arr = [1, 2, 3];
console.log(arr.slice(1, 5)); // 正常運行，返回 [2, 3]

// 使用超出範圍的索引
try {
    console.log(arr.slice(1, -5)); // 會返回 [2, 3]，但不會拋出錯誤
} catch (e) {
    console.error(e); // 不會觸發錯誤
}

// 使用數學運算
function checkNumber(num) {
    if (num < 0 || num > 100) {
        throw new RangeError("數字必須在 0 到 100 的範圍內");
    }
    return num;
}

try {
    console.log(checkNumber(150)); // 會拋出 RangeError
} catch (e) {
    console.error(e.message); // 輸出 "數字必須在 0 到 100 的範圍內"
}
```

## 解釋
- **常見陷阱**: 開發者在處理數組時，可能會誤以為 `slice()` 方法會始終拋出錯誤，實際上它在超出範圍時會返回一個空數組或部分數組。
- **額外注意**: 在使用數學函數時，確保對輸入的數值進行有效性檢查，避免因數值超出範圍而導致的錯誤。

## 一句話總結
RangeError 是 JavaScript 中用於表示數值超出可接受範圍的錯誤類型，對於數據驗證和錯誤處理尤為重要。