<!--
Meta Description: # JavaScript 中的 Document 對象：全面指南 ## 簡介 在 JavaScript 中，`document` 對象是用來操作和控制 HTML 文檔的核心組件之一。它是瀏覽器的 Document Object Model (DOM) 的入口點，使開發者能夠動態地訪問和修改網頁內容。...
Meta Keywords: document, javascript, dom, html, queryselector
-->

# JavaScript 中的 Document 對象：全面指南

## 簡介
在 JavaScript 中，`document` 對象是用來操作和控制 HTML 文檔的核心組件之一。它是瀏覽器的 Document Object Model (DOM) 的入口點，使開發者能夠動態地訪問和修改網頁內容。

## 文檔說明
`document` 對象代表整個 HTML 文檔，提供了多種方法和屬性來訪問和操作 DOM 中的元素。通過 `document`，開發者可以創建、修改或刪除 HTML 元素，並且能夠獲取用戶輸入、改變樣式、添加事件監聽器等。

### 主要功能：
- **獲取和修改元素**：使用 `getElementById`、`getElementsByClassName`、`querySelector` 等方法來選擇和操作 DOM 元素。
- **創建新元素**：通過 `createElement` 方法創建新的 DOM 元素。
- **處理事件**：使用 `addEventListener` 方法來為元素添加事件監聽器。
- **文檔信息**：可透過 `document.title`、`document.URL` 等屬性獲取當前文檔的相關信息。

## 使用範例
### 獲取一個元素
```javascript
let element = document.getElementById('myElement');
console.log(element);
```

### 修改元素內容
```javascript
let heading = document.querySelector('h1');
heading.textContent = '新的標題';
```

### 創建並添加新元素
```javascript
let newDiv = document.createElement('div');
newDiv.textContent = '這是新創建的 div';
document.body.appendChild(newDiv);
```

### 添加事件監聽器
```javascript
let button = document.querySelector('button');
button.addEventListener('click', function() {
    alert('按鈕被點擊了！');
});
```

## 解釋
在使用 `document` 對象時，開發者需要注意以下幾點：

- **DOM 未加載時的訪問**：如果在 DOM 尚未完全加載時嘗試訪問元素，可能會導致 `null` 返回。應使用 `DOMContentLoaded` 事件來確保 DOM 加載完成後再執行代碼。
  
- **選擇器的使用**：`querySelector` 和 `querySelectorAll` 方法提供了強大的選擇器支持，但在性能上可能不如 `getElementById` 或 `getElementsByClassName`。根據需要選擇合適的方法。

- **動態修改**：在動態增刪元素時，需注意可能會影響到事件監聽器的綁定，應考慮使用事件委託來處理事件。

## 總結
`document` 對象是 JavaScript 操作 HTML 文檔的基礎，提供了豐富的方法和屬性來輕鬆地訪問和修改網頁內容。