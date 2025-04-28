<!--
Meta Description: # JavaScript StaticRange：靜態範圍物件的完整指南 ## 簡介 `StaticRange` 是一個 JavaScript 物件，提供一種方式來表示靜態範圍，允許開發者捕捉並處理文檔中的一段文本範圍。此物件在處理 DOM 範圍時特別有用，特別是在執行文本選擇或操作時。 ## 文檔...
Meta Keywords: staticrange, javascript, startcontainer, containerelement, endoffset
-->

# JavaScript StaticRange：靜態範圍物件的完整指南

## 簡介
`StaticRange` 是一個 JavaScript 物件，提供一種方式來表示靜態範圍，允許開發者捕捉並處理文檔中的一段文本範圍。此物件在處理 DOM 範圍時特別有用，特別是在執行文本選擇或操作時。

## 文檔
`StaticRange` 物件的主要目的是提供一個不會隨著 DOM 的變化而變動的範圍。這意味著，即使文檔的結構改變，`StaticRange` 內部持有的開始和結束位置仍然保持不變。這對於需要在特定範圍內執行操作的應用程式來說非常重要。

### 使用方法
要創建一個 `StaticRange` 物件，可以使用以下構造函數：

```javascript
let staticRange = new StaticRange({
    startContainer: containerElement,
    startOffset: 0,
    endContainer: containerElement,
    endOffset: 5
});
```

### 參數說明
- `startContainer`：範圍的開始節點。
- `startOffset`：範圍開始位置的偏移量。
- `endContainer`：範圍的結束節點。
- `endOffset`：範圍結束位置的偏移量。

## 範例
以下是一些使用 `StaticRange` 的基本示例：

### 例子 1：創建靜態範圍
```javascript
const containerElement = document.getElementById('myElement');
const staticRange = new StaticRange({
    startContainer: containerElement,
    startOffset: 0,
    endContainer: containerElement,
    endOffset: 10
});
console.log(staticRange);
```

### 例子 2：檢查範圍
```javascript
const range = new StaticRange({
    startContainer: document.body,
    startOffset: 0,
    endContainer: document.body,
    endOffset: 5
});

console.log(range.startContainer); // 輸出: <body> ...
console.log(range.endOffset); // 輸出: 5
```

## 解釋
在使用 `StaticRange` 時，開發者需要注意以下幾點：
1. **靜態性**：`StaticRange` 的靜態性意味著它不會隨著 DOM 的變更而更新，因此在處理動態頁面時需小心。
2. **範圍的正確性**：提供給 `StaticRange` 的節點和偏移量必須正確，否則可能會導致錯誤或異常行為。
3. **相容性**：`StaticRange` 在部分舊版瀏覽器中可能不被支援，因此在使用之前應確認目標瀏覽器的相容性。

## 總結
`StaticRange` 是一個強大的工具，可以幫助開發者在 JavaScript 中有效地處理和操作靜態文本範圍。