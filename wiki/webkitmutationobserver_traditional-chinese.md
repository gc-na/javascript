<!--
Meta Description: # WebKitMutationObserver: 監控DOM變更的高效解決方案 ## 簡介 WebKitMutationObserver 是一個用於監控DOM（文件物件模型）變更的JavaScript API。它提供一種高效的方式來接收和處理DOM樹的變化，特別適用於需要即時反應變更的應用程式。 ...
Meta Keywords: const, observer, targetnode, webkitmutationobserver, mutation
-->

# WebKitMutationObserver: 監控DOM變更的高效解決方案

## 簡介
WebKitMutationObserver 是一個用於監控DOM（文件物件模型）變更的JavaScript API。它提供一種高效的方式來接收和處理DOM樹的變化，特別適用於需要即時反應變更的應用程式。

## 文檔
### 目的
WebKitMutationObserver 旨在替代舊有的 `Mutation Events` API，提供更高效的DOM變更監控功能。它允許開發者監控特定DOM元素的新增、刪除及屬性變更。

### 使用方法
要使用WebKitMutationObserver，首先需創建一個觀察者實例，並定義一個回調函數，該函數會在指定的DOM變更發生時被調用。然後，使用`observe`方法指定要監控的目標元素及其變更類型。

#### 基本語法：
```javascript
const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
```

#### 參數說明：
- `callback`: 當DOM發生變化時將被調用的函數。該函數接受兩個參數：`mutationsList`（變更列表）和 `observer`（觀察者實例）。
- `targetNode`: 要監控的目標DOM元素。
- `config`: 一個物件，用於指定要監控的變更類型，如 `childList`、`attributes`、`subtree`等。

### 詳細配置選項
- `childList`: 監控目標元素的子元素的新增或刪除。
- `attributes`: 監控目標元素的屬性變更。
- `subtree`: 監控目標元素及其所有子元素的變更。

## 範例
以下是使用 WebKitMutationObserver 的基本範例：

### 例子1：監控子元素的變更
```javascript
const targetNode = document.getElementById('myElement');
const config = { childList: true };

const callback = function(mutationsList, observer) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('子元素已變更');
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// 添加一個新的子元素
const newElement = document.createElement('div');
targetNode.appendChild(newElement);
```

### 例子2：監控屬性變更
```javascript
const targetNode = document.getElementById('myElement');
const config = { attributes: true };

const callback = function(mutationsList, observer) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'attributes') {
            console.log('屬性已變更:', mutation.attributeName);
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// 修改目標元素的屬性
targetNode.setAttribute('data-example', 'newValue');
```

## 解釋
使用 WebKitMutationObserver 時，開發者需要注意以下幾點：
- **性能考量**：雖然 MutationObserver 提供了更高效的監控方式，但不當使用仍可能影響性能，建議僅監控必要的變更。
- **回調函數執行的上下文**：回調函數會在瀏覽器的事件循環中執行，因此如果需要更新UI，請確保這些操作不會阻塞主線程。
- **停止觀察**：當不再需要監控時，應使用 `disconnect` 方法停止觀察，以釋放資源。

## 一句總結
WebKitMutationObserver 是一個高效的API，用於監控DOM的變更，替代了舊的Mutation Events，提供了更好的性能和靈活性。