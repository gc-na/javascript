<!--
Meta Description: # JavaScript 中的 Symbol：獨特的數據類型 ## 簡介 Symbol 是 JavaScript 中的一種基本數據類型，用於創建獨特的識別符，特別適合用於對象的屬性鍵，能有效避免屬性名稱的衝突。 ## 文檔 ### 目的 Symbol 的主要目的是提供一種獨一無二且不可變的識別符，這...
Meta Keywords: symbol, javascript, const, uniquekey, console
-->

# JavaScript 中的 Symbol：獨特的數據類型

## 簡介
Symbol 是 JavaScript 中的一種基本數據類型，用於創建獨特的識別符，特別適合用於對象的屬性鍵，能有效避免屬性名稱的衝突。

## 文檔
### 目的
Symbol 的主要目的是提供一種獨一無二且不可變的識別符，這使得使用者可以在對象中創建私有屬性，防止與其他屬性發生衝突。

### 用法
要創建一個 Symbol，可以使用 `Symbol()` 函數。此函數可以接受一個可選的描述參數，以便於調試，但不會影響 Symbol 的唯一性。

```javascript
const sym1 = Symbol('description');
const sym2 = Symbol('description');
console.log(sym1 === sym2); // false，因為每個 Symbol 都是唯一的
```

### 詳細說明
- **唯一性**：每個 Symbol 都是唯一的，即使它們有相同的描述。
- **不可變性**：Symbol 一經創建，就無法改變其值。
- **作為屬性鍵**：Symbol 可用作對象的屬性鍵，這樣可以避免屬性名稱衝突，特別是在大型代碼庫中。

## 範例
以下是使用 Symbol 的基本範例：

```javascript
// 創建 Symbol
const uniqueKey = Symbol('myUniqueKey');

// 使用 Symbol 作為對象屬性
const myObject = {
    [uniqueKey]: 'value'
};

// 存取 Symbol 屬性
console.log(myObject[uniqueKey]); // 輸出 'value'

// Symbol 不能被轉換為字符串
console.log(String(uniqueKey)); // 輸出 'Symbol(myUniqueKey)'
```

## 解釋
- **常見陷阱**：Symbol 不能被轉換成字符串，因此在需要字符串的地方使用 Symbol 可能會導致錯誤。
- **無法列舉**：使用 `for...in` 和 `Object.keys()` 無法列舉 Symbol 屬性，這意味著它們在對象中是隱藏的，這對於封裝數據非常有用。
- **使用 Symbol.for()**：可以使用 `Symbol.for(key)` 創建全局 Symbol，這樣就可以在不同的執行上下文中共享 Symbol。

## 一句總結
Symbol 是一種 JavaScript 的基本數據類型，用於創建獨特的識別符，特別適合用於避免對象屬性名稱的衝突。