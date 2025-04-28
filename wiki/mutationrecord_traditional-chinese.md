<!--
Meta Description: # MutationRecord: JavaScript 中的變更紀錄 ## 簡介 MutationRecord 是一個用於描述 DOM 變更的物件。它是 MutationObserver 的一部分，主要用來監聽和記錄 DOM 樹的變更，如節點的新增、刪除或屬性變更。這對於追蹤和響應 DOM 變更非...
Meta Keywords: mutation, mutationrecord, dom, mutationobserver, type
-->

# MutationRecord: JavaScript 中的變更紀錄

## 簡介
MutationRecord 是一個用於描述 DOM 變更的物件。它是 MutationObserver 的一部分，主要用來監聽和記錄 DOM 樹的變更，如節點的新增、刪除或屬性變更。這對於追蹤和響應 DOM 變更非常有用。

## 文檔
### 目的
MutationRecord 提供了一種結構化的方式來描述 DOM 變更，幫助開發者理解和管理這些變更的影響。

### 用法
MutationRecord 主要在 MutationObserver 的回調函數中使用。當 DOM 發生變更時，MutationObserver 會接收一個 MutationRecord 陣列作為參數，這些紀錄詳細描述了變更的性質。

### 主要屬性
- `type`: 變更的類型，可能的值包括 `childList`、`attributes` 和 `characterData`。
- `target`: 被變更的目標節點。
- `addedNodes`: 一個 NodeList，包含所有被新增的節點。
- `removedNodes`: 一個 NodeList，包含所有被刪除的節點。
- `previousSibling`: 被變更節點的前一個兄弟節點。
- `nextSibling`: 被變更節點的下一個兄弟節點。
- `attributeName`: 當 type 為 `attributes` 時，表示變更的屬性名稱。
- `attributeNamespace`: 當 type 為 `attributes` 時，表示變更的屬性命名空間。
- `oldValue`: 在變更前的舊值，當 `characterData` 或 `attributes` 變更時可用。

## 範例
以下是使用 MutationRecord 的基本範例：

```javascript
// 創建一個 MutationObserver 實例
const observer = new MutationObserver((mutations) => {
    mutations.forEach((mutation) => {
        console.log(`變更類型: ${mutation.type}`);
        console.log(`目標節點:`, mutation.target);
        if (mutation.type === 'childList') {
            console.log(`新增節點:`, mutation.addedNodes);
            console.log(`刪除節點:`, mutation.removedNodes);
        }
        if (mutation.type === 'attributes') {
            console.log(`變更屬性: ${mutation.attributeName}`);
            console.log(`舊值: ${mutation.oldValue}`);
        }
    });
});

// 設置觀察選項
const config = { attributes: true, childList: true, subtree: true };

// 開始觀察指定的目標節點
const targetNode = document.getElementById('target');
observer.observe(targetNode, config);

// 測試變更
targetNode.setAttribute('data-test', 'test');
targetNode.appendChild(document.createElement('div'));
```

## 說明
使用 MutationRecord 時，開發者應注意以下幾點：
- 確保所觀察的節點存在，否則會導致錯誤。
- 當使用 `oldValue` 時，必須在 MutationObserver 的選項中設置 `attributeOldValue` 為 `true`。
- 監聽大量變更時，可能會影響性能。因此，應謹慎選擇要觀察的屬性和節點。

## 總結
MutationRecord 是一個關鍵的工具，幫助開發者有效地監視和管理 DOM 變更。