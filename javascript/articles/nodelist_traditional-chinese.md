<!--
Meta Description: # NodeList：JavaScript中的節點列表 ## 簡介 NodeList 是一種在 JavaScript 中用來表示一組節點的集合，通常由 DOM 操作返回。它常見於查詢文檔中的元素，並且可以用來進行各種操作，例如遍歷、修改或刪除節點。 ## 文件說明 NodeList 是由多個 Nod...
Meta Keywords: nodelist, childnodes, javascript, dom, const
-->

# NodeList：JavaScript中的節點列表

## 簡介
NodeList 是一種在 JavaScript 中用來表示一組節點的集合，通常由 DOM 操作返回。它常見於查詢文檔中的元素，並且可以用來進行各種操作，例如遍歷、修改或刪除節點。

## 文件說明
NodeList 是由多個 Node 物件組成的集合，這些 Node 物件可以是元素節點、文本節點或註釋節點。NodeList 主要由 `document.querySelectorAll()`、`childNodes` 等方法返回。

### 目的
NodeList 使開發者能夠簡單地操作和處理一組 DOM 節點。

### 用法
NodeList 表示的集合可以通過索引來訪問個別節點，並支持一些常用的方法，如 `forEach()`，但不支持陣列的方法（如 `map()` 或 `filter()`），這一點需要特別注意。

### 主要特性
- **靜態 vs 動態**：NodeList 可以是靜態的（如 `querySelectorAll()` 返回的 NodeList）或動態的（如 `childNodes` 返回的 NodeList）。靜態 NodeList 不會隨著 DOM 的變化而更新，而動態 NodeList 會。
- **遍歷**：NodeList 提供了 `forEach()` 方法來遍歷所有節點。
- **長度屬性**：NodeList 具有 `length` 屬性，可以用來獲取節點的數量。

## 範例
### 基本用法
```javascript
// 獲取所有的 <p> 元素
const paragraphs = document.querySelectorAll('p');

// 遍歷 NodeList
paragraphs.forEach(paragraph => {
    console.log(paragraph.textContent);
});
```

### 使用 childNodes
```javascript
// 獲取特定元素的所有子節點
const parentElement = document.getElementById('parent');
const childNodes = parentElement.childNodes;

// 獲取子節點的數量
console.log(childNodes.length);
```

## 解釋
在使用 NodeList 時，有幾個常見的陷阱：
1. **不支持陣列方法**：雖然 NodeList 看起來像一個陣列，但它不支持陣列的所有方法。若需要使用陣列方法，需將其轉換為陣列。
   ```javascript
   const nodesArray = Array.from(paragraphs);
   const filteredNodes = nodesArray.filter(node => node.textContent.includes('特定字串'));
   ```

2. **動態與靜態的理解**：在使用 `childNodes` 時，注意它會隨著 DOM 的變動而變化，而 `querySelectorAll()` 返回的是靜態的集合。

## 一句總結
NodeList 是 JavaScript 中用來表示一組 DOM 節點的集合，提供便利的方式來操作和遍歷這些節點。