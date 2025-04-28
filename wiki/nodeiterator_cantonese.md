<!--
Meta Description: # NodeIterator 在 JavaScript 中的用法及特性 ## 概要 NodeIterator 是一種用於遍歷 DOM 節點的接口，允許開發者以高效的方式逐個訪問文檔中的節點。 ## 文件說明 NodeIterator 是 DOM 的一部分，提供了一種方便的方法來遍歷結構樹中的節點。使...
Meta Keywords: nodeiterator, dom, nodefilter, document, rootnode
-->

# NodeIterator 在 JavaScript 中的用法及特性

## 概要
NodeIterator 是一種用於遍歷 DOM 節點的接口，允許開發者以高效的方式逐個訪問文檔中的節點。

## 文件說明
NodeIterator 是 DOM 的一部分，提供了一種方便的方法來遍歷結構樹中的節點。使用 NodeIterator，可以在不需要手動維護遍歷狀態的情況下，以簡潔的方式訪問節點。這對於需要檢查或修改大量 DOM 節點的應用程序非常有用。

### 目的
NodeIterator 主要用於在 DOM 中遍歷節點，特別是在需要對節點進行過濾或選擇時。

### 用法
NodeIterator 可以通過 `document.createNodeIterator` 方法創建。使用時，需要指定一個根節點和一個過濾器（NodeFilter），以確定哪些節點應該被遍歷。

```javascript
const iterator = document.createNodeIterator(
  rootNode, 
  NodeFilter.SHOW_ELEMENT, 
  null, 
  false
);
```

#### 參數
- **rootNode**: 從哪一個節點開始遍歷。
- **whatToShow**: 指定要顯示的節點類型（如元素、文本）。
- **filter**: 可選的 NodeFilter，用於進一步過濾節點。
- **entityReferenceExpansion**: 是否展開實體引用，預設為 false。

## 示例
以下是使用 NodeIterator 的基本範例：

```javascript
// 獲取根節點
const rootNode = document.getElementById('myElement');

// 創建 NodeIterator
const iterator = document.createNodeIterator(
  rootNode, 
  NodeFilter.SHOW_ELEMENT, 
  null, 
  false
);

// 遍歷節點
let currentNode;
while (currentNode = iterator.nextNode()) {
  console.log(currentNode.tagName); // 輸出每個元素的標籤名稱
}
```

## 解釋
使用 NodeIterator 時，有幾個常見的陷阱和注意事項：

- **過濾器的使用**: 如果不使用過濾器，將遍歷所有指定類型的節點。過濾器可以使用 NodeFilter 的靜態方法來定義。
- **節點狀態**: 一旦使用 `nextNode` 方法，NodeIterator 的狀態會改變，無法回到之前的節點。
- **性能考量**: 在大規模的 DOM 結構中使用 NodeIterator 可以提升性能，因為它比手動遍歷節點更高效。

## 一句總結
NodeIterator 是一個強大的工具，幫助開發者高效遍歷和操作 DOM 節點。