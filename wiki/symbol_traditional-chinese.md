<!--
Meta Description: # JavaScript 的 Symbol：唯一且不可變的數據類型 ## 概述 在 JavaScript 中，`Symbol` 是一種新的原始數據類型，用於創建唯一的標識符。這使得在對象屬性中使用 Symbol 提供了一種避免名稱衝突的方式，並能夠創建私有屬性。 ## 文檔 ### 目的 `Symb...
Meta Keywords: symbol, javascript, uniquekey, const, object
-->

# JavaScript 的 Symbol：唯一且不可變的數據類型

## 概述
在 JavaScript 中，`Symbol` 是一種新的原始數據類型，用於創建唯一的標識符。這使得在對象屬性中使用 Symbol 提供了一種避免名稱衝突的方式，並能夠創建私有屬性。

## 文檔
### 目的
`Symbol` 的主要目的是提供一種生成唯一標識符的方法，這些標識符可以用作對象屬性的鍵。這在需要確保屬性不會與其他屬性發生衝突時非常有用。

### 用法
要創建一個新的 Symbol，可以使用 `Symbol()` 函數，並且可以選擇性地傳遞一個描述字符串，這有助於調試，但不影響 Symbol 的唯一性。

```javascript
const symbol1 = Symbol('描述');
const symbol2 = Symbol('描述');

console.log(symbol1 === symbol2); // false
```

### 詳細說明
- **唯一性**：每次調用 `Symbol()` 都會返回一個新的、唯一的 Symbol，即使描述相同。
- **不可變性**：Symbol 的值是不可變的，無法被更改。
- **屬性鍵**：可以將 Symbol 用作對象的屬性鍵，這樣做的屬性不會出現在 `for...in` 循環中，也不會被 `Object.keys()` 方法列出。

## 示例
以下是使用 `Symbol` 的基本示例：

```javascript
const uniqueKey = Symbol('uniqueKey');

const myObject = {
    [uniqueKey]: '這是一個私有屬性'
};

console.log(myObject[uniqueKey]); // '這是一個私有屬性'
console.log(Object.keys(myObject)); // []
```

在上面的示例中，`uniqueKey` 是一個 Symbol，並且它的值不會在 `Object.keys()` 的結果中出現。

## 解釋
- **常見陷阱**：使用 Symbol 作為對象屬性鍵時，必須注意 Symbol 不會出現在常規屬性列表中。如果需要遍歷所有屬性，應使用 `Object.getOwnPropertySymbols()`。
- **與字符串的區別**：Symbol 與字符串不同，即使描述相同，Symbol 仍然是唯一的。這使得它適合用於需要獨特鍵的情況。

## 一句總結
`Symbol` 是 JavaScript 的一種原始數據類型，用於創建唯一且不可變的標識符，能夠有效避免對象屬性之間的名稱衝突。