<!--
Meta Description: # JavaScript Boolean：深入了解布爾值 ## 概述 布爾值（Boolean）是JavaScript中的一種基本數據類型，用於表示真（true）或假（false）兩種狀態。它們在條件判斷和控制流中扮演著至關重要的角色。 ## 文檔 ### 目的 布爾值主要用於控制程序的邏輯流。例如，...
Meta Keywords: true, let, boolean, false, javascript
-->

# JavaScript Boolean：深入了解布爾值

## 概述
布爾值（Boolean）是JavaScript中的一種基本數據類型，用於表示真（true）或假（false）兩種狀態。它們在條件判斷和控制流中扮演著至關重要的角色。

## 文檔
### 目的
布爾值主要用於控制程序的邏輯流。例如，在`if`語句、`while`循環和其他邏輯運算中，布爾值幫助決定代碼的執行路徑。

### 使用方法
在JavaScript中，布爾值可以通過以下方式創建：
- 直接使用`true`或`false`
- 使用`Boolean()`函數將其他數據類型轉換為布爾值

```javascript
let isActive = true;  // 直接賦值
let isLoggedIn = false; // 直接賦值

// 使用 Boolean() 函數
let isEmpty = Boolean(""); // false
let isNonEmpty = Boolean("Hello"); // true
```

### 詳細說明
布爾值的運算通常涉及邏輯運算符，例如：
- `&&`（邏輯與）
- `||`（邏輯或）
- `!`（邏輯非）

這些運算符用於組合或反轉布爾值，以進行更複雜的邏輯判斷。

## 示例
以下是一些簡單的布爾值用法示例：

```javascript
let a = 5;
let b = 10;

// 使用布爾表達式
if (a < b) {
    console.log("a 小於 b"); // 這行會執行
}

let isAdult = true;
let canVote = isAdult && true; // canVote 將是 true
console.log(canVote); // 輸出：true
```

## 說明
在使用布爾值時，有幾個常見的陷阱：
1. **類型轉換**：某些非布爾數據類型會被自動轉換為布爾值。例如，`0`、`""`（空字符串）、`null`和`undefined`都會被轉換為`false`，而其他任何值都會被轉換為`true`。
2. **邏輯運算符的短路評估**：`&&`和`||`運算符在評估時會進行短路，這意味著如果第一個操作數已經確定了結果，則不會評估第二個操作數。

## 總結
布爾值是JavaScript中一種重要的數據類型，用於表示條件邏輯的真或假。