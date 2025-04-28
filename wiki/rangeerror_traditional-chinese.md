<!--
Meta Description: # JavaScript 中的 RangeError：範圍錯誤的詳細說明 ## 摘要 在 JavaScript 中，`RangeError` 是一種內建的錯誤類型，當數值超出其有效範圍或無法執行某些操作時，會引發此錯誤。 ## 文檔 ### 目的 `RangeError` 用於表示一個數值不在允許的...
Meta Keywords: rangeerror, javascript, repeat, console, age
-->

# JavaScript 中的 RangeError：範圍錯誤的詳細說明

## 摘要
在 JavaScript 中，`RangeError` 是一種內建的錯誤類型，當數值超出其有效範圍或無法執行某些操作時，會引發此錯誤。

## 文檔
### 目的
`RangeError` 用於表示一個數值不在允許的範圍內，通常出現在數學運算、陣列操作或方法調用中，當參數超出預期的範圍時會拋出此錯誤。

### 用法
在 JavaScript 中，`RangeError` 主要用於以下情況：
- 當函數的參數超出指定的範圍。
- 在處理陣列時，索引超出其界限。
- 當使用 `String.prototype.repeat()` 方法時，重複次數超過最大限制。

### 詳細信息
`RangeError` 是 `Error` 的一個子類型，可以使用 `new RangeError(message)` 來創建一個新的範圍錯誤物件。這個物件可以接受一個可選的錯誤訊息作為參數。

```javascript
throw new RangeError("這是一個範圍錯誤");
```

## 示例
以下是一些 `RangeError` 的基本用法示例：

### 範例 1：陣列索引超出範圍
```javascript
let arr = [1, 2, 3];
console.log(arr[5]); // undefined，並不會拋出錯誤，但會返回 undefined
```

### 範例 2：數學計算
```javascript
function setAge(age) {
    if (age < 0 || age > 130) {
        throw new RangeError("年齡必須在 0 到 130 之間");
    }
    return age;
}

try {
    setAge(150);
} catch (e) {
    console.error(e); // 輸出 RangeError: 年齡必須在 0 到 130 之間
}
```

### 範例 3：使用 String.prototype.repeat()
```javascript
try {
    let str = "Hello";
    console.log(str.repeat(-1)); // 將拋出 RangeError
} catch (e) {
    console.error(e); // 輸出 RangeError: 重複次數必須是非負整數
}
```

## 解釋
常見的陷阱包括：
- 忽略範圍檢查，直接使用不受限制的數值，這會導致 `RangeError`。
- 在使用 `repeat()` 方法時，必須確保傳入的參數是非負整數，否則會拋出錯誤。
- 在處理陣列時，應該小心索引的使用，避免訪問不存在的元素。

## 一句話總結
`RangeError` 是一種專門用於表示數值不在有效範圍內的錯誤類型，常見於數學運算和陣列操作中。