<!--
Meta Description: # HTMLDocument：JavaScript 中的網頁結構與操作 ## 概述 HTMLDocument 是一個代表整個 HTML 文檔的對象，透過 JavaScript，開發者可以輕鬆地操作和修改網頁內容、樣式及結構。 ## 文檔 HTMLDocument 對象是瀏覽器環境中 DOM（文件對象...
Meta Keywords: document, htmldocument, javascript, dom, html
-->

# HTMLDocument：JavaScript 中的網頁結構與操作

## 概述
HTMLDocument 是一個代表整個 HTML 文檔的對象，透過 JavaScript，開發者可以輕鬆地操作和修改網頁內容、樣式及結構。

## 文檔
HTMLDocument 對象是瀏覽器環境中 DOM（文件對象模型）的核心部分。它提供了一系列方法和屬性，讓開發者能夠訪問和操作 HTML 文檔的各個部分。

### 目的
HTMLDocument 主要用於以下目的：
- 獲取和修改文檔的元素
- 操作文檔的結構
- 監聽和處理事件

### 使用方法
在 JavaScript 中，HTMLDocument 通常通過 `document` 對象訪問。以下是一些常見的屬性和方法：

- **document.getElementById(id)**：根據 ID 獲取單個元素。
- **document.getElementsByClassName(className)**：根據類名獲取一組元素。
- **document.querySelector(selector)**：根據 CSS 選擇器獲取單個元素。
- **document.querySelectorAll(selector)**：根據 CSS 選擇器獲取一組元素。
- **document.createElement(tagName)**：創建一個新的 HTML 元素。

## 範例
以下是一些 HTMLDocument 的基本使用範例：

### 獲取元素
```javascript
// 根據 ID 獲取元素
let header = document.getElementById('header');
console.log(header);
```

### 修改內容
```javascript
// 修改元素的內容
let paragraph = document.getElementById('paragraph');
paragraph.innerText = '這是修改後的段落內容。';
```

### 創建和添加元素
```javascript
// 創建新元素並添加到文檔
let newDiv = document.createElement('div');
newDiv.innerText = '這是一個新創建的 DIV 元素。';
document.body.appendChild(newDiv);
```

## 解釋
在使用 HTMLDocument 時，開發者常面臨一些常見的問題和注意事項：
- **元素未找到**：使用 `getElementById` 或其他方法時，確保該元素在 DOM 中存在，否則會返回 `null`。
- **DOM 更新**：在操作 DOM 時，確保在文檔完全加載後進行。可以使用 `DOMContentLoaded` 事件來確保文檔已加載。
- **性能問題**：對於大量 DOM 操作，應考慮性能影響。批量插入或使用文檔片段可以提高效率。

## 總結
HTMLDocument 是 JavaScript 操作 HTML 文檔的基礎對象，允許開發者動態地獲取和修改網頁內容。