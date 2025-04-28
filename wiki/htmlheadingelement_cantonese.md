<!--
Meta Description: # HTMLHeadingElement 在 JavaScript 中的使用 ## 概述 HTMLHeadingElement 是一個表示 HTML 標題元素（如 `<h1>` 到 `<h6>`）的介面，主要用於定義頁面的標題和層次結構。在 JavaScript 中，可以通過 DOM 操作來訪問和操...
Meta Keywords: javascript, htmlheadingelement, 標題元素, document, queryselector
-->

# HTMLHeadingElement 在 JavaScript 中的使用

## 概述
HTMLHeadingElement 是一個表示 HTML 標題元素（如 `<h1>` 到 `<h6>`）的介面，主要用於定義頁面的標題和層次結構。在 JavaScript 中，可以通過 DOM 操作來訪問和操作這些元素。

## 文檔
HTMLHeadingElement 提供了一些屬性和方法來控制標題元素的行為。這些元素主要用於改善網頁的可讀性和 SEO（搜尋引擎優化），因為它們幫助搜索引擎理解內容的結構。

### 屬性
- `innerText`：獲取或設置標題元素的文本內容。
- `style`：用於改變標題元素的 CSS 樣式。
- `className`：獲取或設置標題元素的 CSS 類名。

### 方法
- `focus()`：將焦點設置到標題元素上。
- `blur()`：移除標題元素的焦點。

### 使用
要使用 HTMLHeadingElement，首先需要通過 JavaScript 獲取對應的標題元素。例如，可以使用 `document.querySelector()` 或 `document.getElementById()` 方法來獲取指定的標題元素，然後進行操作。

## 例子
以下是一些基本的使用示例：

### 例子 1：獲取和設置標題文本
```javascript
// 獲取 h1 標題元素
let heading = document.querySelector('h1');

// 獲取標題文本
console.log(heading.innerText); // 輸出當前 h1 的文本

// 設置新的標題文本
heading.innerText = "新的標題";
```

### 例子 2：改變標題樣式
```javascript
// 獲取 h2 標題元素
let heading2 = document.querySelector('h2');

// 設置樣式
heading2.style.color = "blue";
heading2.style.fontSize = "24px";
```

### 例子 3：聚焦和失去焦點
```javascript
// 獲取 h3 標題元素
let heading3 = document.querySelector('h3');

// 聚焦 h3 標題
heading3.focus();

// 失去焦點
heading3.blur();
```

## 解釋
在使用 HTMLHeadingElement 時，有一些常見的陷阱需要注意：
- 確保在 DOM 完全加載後再進行操作，否則可能會導致找不到元素。
- 確認所選擇的標題元素存在於文檔中，否則會返回 null。
- 語法錯誤或拼寫錯誤會導致 JavaScript 無法執行預期的操作。

## 一句總結
HTMLHeadingElement 讓開發者能夠通過 JavaScript 動態操作 HTML 標題元素，從而改善網頁的結構和可讀性。