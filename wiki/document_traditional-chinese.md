<!--
Meta Description: # JavaScript中的Document物件：網頁操作的核心 ## 摘要 JavaScript中的`document`物件是瀏覽器提供的一個全局物件，允許開發者訪問和操作HTML和XML文檔的內容與結構。它是DOM（文檔物件模型）的入口，提供了多種方法和屬性來進行網頁元素的動態處理。 ## 文檔...
Meta Keywords: document, title, getelementbyid, javascript, newparagraph
-->

# JavaScript中的Document物件：網頁操作的核心

## 摘要
JavaScript中的`document`物件是瀏覽器提供的一個全局物件，允許開發者訪問和操作HTML和XML文檔的內容與結構。它是DOM（文檔物件模型）的入口，提供了多種方法和屬性來進行網頁元素的動態處理。

## 文檔
### 目的
`document`物件是JavaScript中與網頁互動的核心，提供了訪問和修改DOM的能力。開發者可以使用它來選取元素、創建新元素、刪除元素、處理事件等。

### 使用方式
在JavaScript中，`document`物件通常是自動可用的，無需進行額外的初始化。開發者可以直接使用`document`來進行操作。

### 詳細信息
- **屬性**：
  - `document.title`：獲取或設置文檔的標題。
  - `document.body`：獲取文檔的主體元素。
  - `document.getElementById(id)`：根據ID獲取元素。
  - `document.querySelector(selector)`：根據CSS選擇器獲取元素。

- **方法**：
  - `document.createElement(tagName)`：創建一個新的HTML元素。
  - `document.appendChild(node)`：將一個節點添加到指定的父節點。
  - `document.removeChild(node)`：從其父節點中刪除一個節點。

## 示例
### 獲取和修改標題
```javascript
// 獲取當前文檔的標題
console.log(document.title);

// 修改文檔的標題
document.title = "新的標題";
```

### 創建和添加元素
```javascript
// 創建一個新的段落元素
const newParagraph = document.createElement("p");
newParagraph.textContent = "這是一個新段落。";

// 將新段落添加到文檔的主體
document.body.appendChild(newParagraph);
```

### 獲取元素並修改內容
```javascript
// 根據ID獲取元素並修改其內容
const element = document.getElementById("myElement");
element.textContent = "已更新的內容";
```

## 解釋
使用`document`物件時，開發者需注意以下幾點：
- 確保DOM已完全加載。對於在DOM加載之前執行的操作，應使用`DOMContentLoaded`事件。
- 使用`getElementById`方法時，ID必須是唯一的，否則可能會導致選擇錯誤的元素。
- 在操作DOM時，可能會導致性能下降，特別是大量的插入和刪除操作，應考慮批量處理或使用文檔片段（DocumentFragment）。

## 一句話總結
JavaScript中的`document`物件是操作網頁內容和結構的關鍵，提供了多種方法來動態管理DOM元素。