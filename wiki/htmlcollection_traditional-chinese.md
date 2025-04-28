<!--
Meta Description: # HTMLCollection: JavaScript 中的 HTML 集合 ## 摘要 HTMLCollection 是一種 JavaScript 對象，代表一組 HTML 元素。它通常由 DOM 方法返回，允許開發者方便地操作和訪問文檔中的元素集合。 ## 文檔 HTMLCollection ...
Meta Keywords: htmlcollection, document, dom, javascript, html
-->

# HTMLCollection: JavaScript 中的 HTML 集合

## 摘要
HTMLCollection 是一種 JavaScript 對象，代表一組 HTML 元素。它通常由 DOM 方法返回，允許開發者方便地操作和訪問文檔中的元素集合。

## 文檔
HTMLCollection 是一種動態集合，主要用於存儲和操作 DOM 中的元素。這種集合類型可以用於各種場景，例如使用 `document.getElementsByTagName()` 或 `document.getElementsByClassName()` 來獲取特定標籤或類別的元素。

### 主要特點
- **動態更新**：HTMLCollection 會隨著 DOM 的變化而即時更新。
- **索引訪問**：可以使用數字索引來訪問集合中的元素，如 `collection[0]`。
- **for 迴圈支持**：可以使用 `for` 迴圈遍歷集合中的每個元素。

### 使用方法
要創建或獲取 HTMLCollection，可以使用以下方法：
- `document.getElementsByTagName(tagName)`
- `document.getElementsByClassName(className)`
- `document.forms`：返回文檔中所有表單的集合。
- `document.images`：返回文檔中所有圖像的集合。

## 例子
```javascript
// 獲取文檔中所有的 <p> 標籤
const paragraphs = document.getElementsByTagName('p');

// 訪問第一個 <p> 元素
console.log(paragraphs[0].textContent);

// 獲取文檔中所有的帶有 "highlight" 類別的元素
const highlights = document.getElementsByClassName('highlight');

// 遍歷所有的高亮元素並打開控制台輸出
for (let i = 0; i < highlights.length; i++) {
    console.log(highlights[i].textContent);
}
```

## 解釋
在使用 HTMLCollection 時，開發者應注意以下幾點：
- **不支持 Array 方法**：HTMLCollection 不是一個真正的數組，因此無法直接使用如 `forEach` 等數組方法。如果需要使用這些方法，可以將其轉換為數組，例如使用 `Array.from()`。
- **動態性**：HTMLCollection 是動態的，這意味著如果在 DOM 中添加或刪除元素，HTMLCollection 會自動更新，這可能會影響迴圈操作。
- **索引範圍**：訪問不存在的索引會返回 `undefined`，而不是引發錯誤。

## 一句總結
HTMLCollection 是一種動態集合，用於表示和操作文檔中的一組 HTML 元素。