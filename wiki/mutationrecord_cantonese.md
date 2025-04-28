<!--
Meta Description: # MutationRecord：JavaScript 中的變更記錄物件 ## 概述 MutationRecord 是一種在 JavaScript 中用於描述 DOM 變更的物件，主要用於 MutationObserver API。它可以幫助開發者追蹤並響應 DOM 結構的變更，例如節點的新增、刪除...
Meta Keywords: type, mutation, mutationrecord, dom, mutationobserver
-->

# MutationRecord：JavaScript 中的變更記錄物件

## 概述
MutationRecord 是一種在 JavaScript 中用於描述 DOM 變更的物件，主要用於 MutationObserver API。它可以幫助開發者追蹤並響應 DOM 結構的變更，例如節點的新增、刪除或屬性變更。

## 文檔
MutationRecord 物件提供了一個簡單的接口來描述 DOM 變更的詳情。當使用 MutationObserver 監聽 DOM 的變更時，每當變更發生，MutationObserver 就會生成一個或多個 MutationRecord 物件，這些物件包含了變更的相關信息。

### 主要屬性
1. **type**：指示變更的類型，可能的值包括 `"childList"`、`"attributes"` 或 `"characterData"`。
2. **target**：指向產生變更的節點。
3. **addedNodes**：一個 NodeList，包含所有新增的節點（僅在 type 為 "childList" 時有效）。
4. **removedNodes**：一個 NodeList，包含所有刪除的節點（僅在 type 為 "childList" 時有效）。
5. **previousSibling**：在新增或刪除節點時，指向該節點的前一個兄弟節點，若無則為 null。
6. **nextSibling**：在新增或刪除節點時，指向該節點的下一個兄弟節點，若無則為 null。
7. **attributeName**：在屬性變更時，指示被變更的屬性名稱（僅在 type 為 "attributes" 時有效）。
8. **attributeNamespace**：對於屬性變更時，指示屬性的命名空間（僅在 type 為 "attributes" 時有效）。

## 範例
以下是一個使用 MutationObserver 和 MutationRecord 的基本範例：

```javascript
// 創建一個 MutationObserver 實例
const observer = new MutationObserver((mutationsList) => {
    for (const mutation of mutationsList) {
        console.log('變更類型:', mutation.type);
        console.log('目標節點:', mutation.target);
        
        if (mutation.type === 'childList') {
            console.log('新增節點:', mutation.addedNodes);
            console.log('刪除節點:', mutation.removedNodes);
        } else if (mutation.type === 'attributes') {
            console.log('變更屬性:', mutation.attributeName);
        }
    }
});

// 配置觀察選項
const config = { childList: true, attributes: true };

// 開始觀察目標節點
const targetNode = document.getElementById('target');
observer.observe(targetNode, config);

// 進行一些變更以觸發觀察者
const newElement = document.createElement('div');
targetNode.appendChild(newElement); // 觸發 childList 變更
targetNode.setAttribute('data-sample', 'value'); // 觸發 attributes 變更
```

## 解釋
在使用 MutationRecord 時，常見的陷阱包括：
- 確保選擇正確的觀察選項，否則可能會錯過重要的變更。
- 注意在處理新增或刪除節點時，`addedNodes` 和 `removedNodes` 可能是空的 NodeList。
- 使用 `previousSibling` 和 `nextSibling` 時需確認節點存在，否則會返回 null。

## 一句總結
MutationRecord 是 JavaScript 中用於描述 DOM 變更的物件，幫助開發者追蹤和響應各種 DOM 結構的變更。