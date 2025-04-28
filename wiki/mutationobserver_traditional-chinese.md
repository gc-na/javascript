<!--
Meta Description: # MutationObserver：JavaScript 的高效 DOM 變更監控器 ## 概述 MutationObserver 是一個強大的 JavaScript API，用於監控和響應 DOM 樹的變更。它允許開發者在不影響性能的情況下，得知何時發生了結構性變更，如節點添加、刪除或屬性更改。...
Meta Keywords: mutationobserver, const, dom, mutation, javascript
-->

# MutationObserver：JavaScript 的高效 DOM 變更監控器

## 概述
MutationObserver 是一個強大的 JavaScript API，用於監控和響應 DOM 樹的變更。它允許開發者在不影響性能的情況下，得知何時發生了結構性變更，如節點添加、刪除或屬性更改。

## 文檔
MutationObserver 提供了一種非同步的方式來監控 DOM 的變化。這對於需要立即響應 DOM 更新的應用程式（如 SPA）來說，特別有用。

### 目的
MutationObserver 的主要目的是提供一種高效的方式來偵測 DOM 變更，而不需要使用舊版的 `Mutation Events`，這些事件會影響性能。

### 使用
要使用 MutationObserver，您需要執行以下步驟：

1. **創建一個 MutationObserver 實例**：
   ```javascript
   const observer = new MutationObserver(callback);
   ```

2. **定義回調函數**：
   當 DOM 變更時，這個函數會被調用。
   ```javascript
   const callback = function(mutationsList, observer) {
       for (let mutation of mutationsList) {
           if (mutation.type === 'childList') {
               console.log('A child node has been added or removed.');
           }
           else if (mutation.type === 'attributes') {
               console.log('The ' + mutation.attributeName + ' attribute was modified.');
           }
       }
   };
   ```

3. **指定要觀察的目標和選項**：
   ```javascript
   const targetNode = document.getElementById('some-id');
   const config = { attributes: true, childList: true, subtree: true };

   observer.observe(targetNode, config);
   ```

4. **停止觀察**：
   當不再需要監控時，可以使用 `disconnect()` 方法停止。
   ```javascript
   observer.disconnect();
   ```

## 範例
### 基本使用範例
以下是一個簡單的範例，監控一個元素的子節點和屬性變更：

```html
<div id="target">
    <p>原始內容</p>
</div>

<script>
const targetNode = document.getElementById('target');

const config = { childList: true, subtree: true };

const callback = function(mutationsList) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('子節點已被添加或移除。');
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// 添加一個新的子節點
const newParagraph = document.createElement('p');
newParagraph.textContent = '新內容';
targetNode.appendChild(newParagraph);
</script>
```

## 解釋
### 常見陷阱
- **性能考量**：雖然 MutationObserver 比舊版的 Mutation Events 更高效，但仍應謹慎使用，以免過度監控導致性能下降。
- **非同步性**：回調函數是非同步執行的，這意味著您不能立即在回調中獲取最新的 DOM 狀態。

### 額外註記
- **監控選項**：可以選擇觀察屬性、子節點、以及子樹的變更。根據需求調整選項以最佳化性能。
- **多個觀察者**：可以為不同的元素創建多個 MutationObserver 實例，從而實現細粒度的控制。

## 總結
MutationObserver 是一個高效的 JavaScript API，用於監控 DOM 變更，適合需要響應性強的網頁應用程式。