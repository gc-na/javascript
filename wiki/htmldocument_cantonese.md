<!--
Meta Description: # HTMLDocument：JavaScript 中的主要物件 ## 概述 HTMLDocument 是 JavaScript 中用於操作和處理網頁文檔的主要物件。它代表整個 HTML 文檔，並提供了一系列方法和屬性，讓開發者能夠輕鬆地訪問和修改網頁內容。 ## 文件說明 HTMLDocument...
Meta Keywords: htmldocument, document, javascript, html, dom
-->

# HTMLDocument：JavaScript 中的主要物件

## 概述
HTMLDocument 是 JavaScript 中用於操作和處理網頁文檔的主要物件。它代表整個 HTML 文檔，並提供了一系列方法和屬性，讓開發者能夠輕鬆地訪問和修改網頁內容。

## 文件說明
HTMLDocument 物件是 Document 物件的一個實例，通常通過 `document` 變量來訪問。這個物件是瀏覽器加載的 HTML 文檔的表示，開發者可以使用它來與網頁的結構和內容進行互動。HTMLDocument 提供了許多方法，例如查找元素、創建新的元素、刪除元素、以及更改元素的屬性等。

### 目的
HTMLDocument 的主要目的是讓開發者能夠以編程方式操作網頁的內容和結構，從而實現動態的用戶體驗。

### 使用方法
使用 HTMLDocument，開發者可以：
- 獲取和修改 DOM 樹中的元素
- 添加和刪除節點
- 綁定事件處理程序
- 更改樣式和屬性

### 詳細資訊
HTMLDocument 物件的一些重要屬性和方法包括：
- `document.getElementById(id)`：根據 id 獲取對應的元素。
- `document.querySelector(selector)`：使用 CSS 選擇器獲取元素。
- `document.createElement(tagName)`：創建一個新的 HTML 元素。
- `document.body`：獲取網頁的主體元素。

## 範例
以下是一些使用 HTMLDocument 的基本範例：

### 獲取元素
```javascript
let header = document.getElementById('header');
console.log(header.textContent);
```

### 創建並添加元素
```javascript
let newDiv = document.createElement('div');
newDiv.textContent = '這是一個新創建的 div 元素';
document.body.appendChild(newDiv);
```

### 修改樣式
```javascript
let paragraph = document.querySelector('p');
paragraph.style.color = 'blue';
```

## 解釋
在使用 HTMLDocument 時，有些常見的問題和注意事項需要留意：
- 確保在 DOM 完全加載後再執行 JavaScript 代碼，否則可能會導致無法獲取元素。
- 使用 `querySelector` 時，CSS 選擇器需要正確，否則可能無法獲取到預期的元素。
- 使用 `createElement` 創建新元素後，必須將其附加到 DOM 中，否則它不會顯示在頁面上。

## 一句總結
HTMLDocument 是 JavaScript 中操作和管理網頁內容的核心物件，允許開發者實現動態和交互式的用戶體驗。