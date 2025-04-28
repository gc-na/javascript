<!--
Meta Description: # JavaScript 字串 (String)：全面指南 ## 概述 在 JavaScript 中，字串是一種用來表示文本的數據類型。字串可以包含字母、數字、符號和空白，是處理文本數據的基本工具。 ## 文檔 字串在 JavaScript 中是不可變的，這意味著一旦創建後，字串的內容無法更改。字串...
Meta Keywords: hello, world, greeting, javascript, console
-->

# JavaScript 字串 (String)：全面指南

## 概述
在 JavaScript 中，字串是一種用來表示文本的數據類型。字串可以包含字母、數字、符號和空白，是處理文本數據的基本工具。

## 文檔
字串在 JavaScript 中是不可變的，這意味著一旦創建後，字串的內容無法更改。字串可以使用單引號、雙引號或反引號（模板字串）來創建。字串提供了多種方法來操作文本，例如查找、替換和分割。

### 用法
創建字串的基本語法如下：

```javascript
let str1 = 'Hello, World!'; // 使用單引號
let str2 = "Hello, World!"; // 使用雙引號
let str3 = `Hello, World!`;  // 使用反引號（模板字串）
```

### 字串方法
- `length`: 獲取字串的長度。
- `charAt(index)`: 獲取指定索引的字元。
- `indexOf(substring)`: 返回子字串首次出現的位置。
- `slice(start, end)`: 返回從 start 到 end 的字串片段。
- `toUpperCase()`: 將字串轉換為大寫。
- `toLowerCase()`: 將字串轉換為小寫。

## 範例
以下示範了如何使用字串及其方法：

```javascript
let greeting = "Hello, World!";
console.log(greeting.length); // 13
console.log(greeting.charAt(7)); // W
console.log(greeting.indexOf("World")); // 7
console.log(greeting.slice(0, 5)); // Hello
console.log(greeting.toUpperCase()); // HELLO, WORLD!
console.log(greeting.toLowerCase()); // hello, world!
```

## 解釋
在使用字串時，開發者常會遇到以下常見問題：

1. **索引從零開始**：字串的索引是從零開始的，這意味著第一個字元的索引是 0。
2. **不可變性**：字串一旦被創建，其內容無法直接更改。如果需要變更，必須創建一個新的字串。
3. **模板字串**：使用反引號的模板字串可使多行字串和插入變量變得簡單，注意在使用時確保引號正確。

## 一行總結
JavaScript 字串是一種不可變的文本數據格式，提供多種方法來處理和操作文本。