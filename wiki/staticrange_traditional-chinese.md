<!--
Meta Description: # StaticRange：JavaScript 中的靜態範圍對象 ## 摘要 `StaticRange` 是一個 JavaScript 對象，用於表示靜態的文本範圍，並提供了對該範圍內文本的讀取和操作功能。它在處理 DOM 節點和文本選擇方面發揮著重要作用，特別是在編輯器和文本處理應用中。 ## ...
Meta Keywords: staticrange, startcontainer, endcontainer, javascript, startoffset
-->

# StaticRange：JavaScript 中的靜態範圍對象

## 摘要
`StaticRange` 是一個 JavaScript 對象，用於表示靜態的文本範圍，並提供了對該範圍內文本的讀取和操作功能。它在處理 DOM 節點和文本選擇方面發揮著重要作用，特別是在編輯器和文本處理應用中。

## 文檔
`StaticRange` 的主要用途是定義一個靜態範圍，這個範圍包含一個或多個 DOM 節點內的文本。該對象可以用於獲取範圍內的文本內容、範圍的起始和結束位置等信息。其基本構造函數如下：

```javascript
new StaticRange(init);
```

### 參數
- `init`：一個對象，包含以下屬性：
  - `startContainer`：範圍的起始節點。
  - `startOffset`：範圍起始節點中的偏移量。
  - `endContainer`：範圍的結束節點。
  - `endOffset`：範圍結束節點中的偏移量。

### 屬性
- `startContainer`：返回範圍的起始容器。
- `startOffset`：返回範圍的起始偏移量。
- `endContainer`：返回範圍的結束容器。
- `endOffset`：返回範圍的結束偏移量。
- `collapsed`：如果範圍未展開，則返回 `true`，否則返回 `false`。

## 示例
以下是 `StaticRange` 的基本用法示例：

```javascript
// 獲取一個 DOM 節點
const element = document.getElementById('myElement');

// 創建一個靜態範圍
const staticRange = new StaticRange({
    startContainer: element.firstChild,
    startOffset: 0,
    endContainer: element.firstChild,
    endOffset: 5
});

// 輸出範圍的相關信息
console.log(staticRange.startContainer); // 輸出起始容器
console.log(staticRange.startOffset);     // 輸出起始偏移量
console.log(staticRange.endContainer);     // 輸出結束容器
console.log(staticRange.endOffset);        // 輸出結束偏移量
```

## 解釋
在使用 `StaticRange` 時，有幾個常見的陷阱和注意事項：

1. **範圍的有效性**：確保 `startContainer` 和 `endContainer` 是有效的 DOM 節點，否則會導致錯誤。
2. **偏移量的範圍**：`startOffset` 和 `endOffset` 必須在對應容器的文本長度範圍內，否則會引發異常。
3. **折疊範圍**：如果 `startContainer` 和 `endContainer` 相同且偏移量相同，則範圍是折疊的，這可能會影響後續操作。

## 一句總結
`StaticRange` 是用於表示和操作靜態文本範圍的 JavaScript 對象，對於文本處理和編輯器應用至關重要。