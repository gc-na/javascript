<!--
Meta Description: # WebKitMutationObserver：JavaScript 的 DOM 變更觀察器 ## 概述 WebKitMutationObserver 是一個用於監聽 DOM 標記變更的 JavaScript API，讓開發者能夠高效地觀察和響應頁面中元素的變化。 ## 文檔 ### 目的 Web...
Meta Keywords: const, mutation, targetnode, mutationobserver, observer
-->

# WebKitMutationObserver：JavaScript 的 DOM 變更觀察器

## 概述
WebKitMutationObserver 是一個用於監聽 DOM 標記變更的 JavaScript API，讓開發者能夠高效地觀察和響應頁面中元素的變化。

## 文檔
### 目的
WebKitMutationObserver 的主要目的是取代舊有的 `Mutation Events`，以提供更高效的方式來監視 DOM 的變更。它可以監聽結構變更、屬性變更以及文本內容的變更，並在變化發生時觸發回調函數。

### 使用方法
要使用 WebKitMutationObserver，需遵循以下步驟：

1. 創建一個 `MutationObserver` 實例，並傳入一個回調函數。
2. 使用 `observe` 方法指定要觀察的目標節點和選項。
3. 在不再需要觀察時，可以調用 `disconnect` 方法停止觀察。

#### 語法範例：
```javascript
const observer = new MutationObserver((mutationsList, observer) => {
    for (let mutation of mutationsList) {
        console.log(mutation);
    }
});

const targetNode = document.getElementById('target');
const config = { attributes: true, childList: true, subtree: true };

observer.observe(targetNode, config);
```

### 詳細信息
- **回調函數**：當監察的元素發生變更時，回調函數會被調用，並接收一個 `MutationRecord` 的陣列，該陣列包含了發生的所有變更。
- **配置選項**：可以指定 `attributes`、`childList`、`subtree` 等選項來控制觀察的具體內容。
- **性能考量**：相比於舊的 `Mutation Events`，`MutationObserver` 提供了更好的性能，因為它是異步執行的，並且在同一事件循環中批量處理變更。

## 範例
以下是一些基本的使用範例：

### 觀察屬性變更
```javascript
const targetNode = document.getElementById('example');
const config = { attributes: true };

const callback = function(mutationsList) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'attributes') {
            console.log(`The ${mutation.attributeName} attribute was modified.`);
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// 改變屬性以觸發觀察器
targetNode.setAttribute('data-changed', 'true');
```

### 觀察子節點變更
```javascript
const targetNode = document.getElementById('example');
const config = { childList: true };

const callback = function(mutationsList) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('A child node has been added or removed.');
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// 改變子節點以觸發觀察器
const newChild = document.createElement('div');
targetNode.appendChild(newChild);
```

## 解釋
- **常見問題**：使用 `MutationObserver` 時，應注意避免無限循環的情況，例如在回調函數內部修改觀察的 DOM 會導致再次觸發回調。
- **性能問題**：雖然 `MutationObserver` 提供了高效的變更監視，但仍需謹慎使用，特別是在觀察大量的 DOM 元素時，建議適當調整選項以減少性能開銷。

## 一行總結
WebKitMutationObserver 是一個高效的 JavaScript API，用於觀察和響應 DOM 標記的變化。