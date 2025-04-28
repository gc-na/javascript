<!--
Meta Description: # ResizeObserver：JavaScript 中的動態元素大小監控器 ## 概述 `ResizeObserver` 是一個 JavaScript API，允許開發者監控 DOM 元素的大小變化，並在尺寸改變時執行回調函數。這對於響應式設計和動態佈局特別有用，能夠在元素大小變化時自動更新界面...
Meta Keywords: resizeobserver, entry, javascript, const, entries
-->

# ResizeObserver：JavaScript 中的動態元素大小監控器

## 概述
`ResizeObserver` 是一個 JavaScript API，允許開發者監控 DOM 元素的大小變化，並在尺寸改變時執行回調函數。這對於響應式設計和動態佈局特別有用，能夠在元素大小變化時自動更新界面。

## 文件說明
### 目的
`ResizeObserver` 主要用於監控特定元素的尺寸變化，讓開發者能夠在這些變化發生時作出即時反應。這對於需要根據元素大小調整樣式或佈局的應用程序來說非常重要。

### 使用方法
要使用 `ResizeObserver`，您需要執行以下步驟：

1. 創建一個 `ResizeObserver` 實例，並傳入一個回調函數。
2. 使用 `observe` 方法監控特定的 DOM 元素。
3. 當元素大小發生改變時，回調函數會自動被調用。

```javascript
const resizeObserver = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log('Element:', entry.target);
        console.log('Width:', entry.contentRect.width);
        console.log('Height:', entry.contentRect.height);
    }
});

const element = document.querySelector('#myElement');
resizeObserver.observe(element);
```

### 詳細說明
- **回調函數**：當監控的元素尺寸改變時，`ResizeObserver` 會調用提供的回調函數，並傳遞一個 `ResizeObserverEntry` 的陣列，該陣列包含所有被觀察元素的相關資訊。
- **解除監控**：當不再需要監控某個元素時，可以使用 `unobserve` 方法停止監控，或者使用 `disconnect` 方法解除所有監控。
- **性能考量**：`ResizeObserver` 會在每次尺寸變化時觸發回調，這可能會影響性能，特別是在大量元素被監控時。因此，需要謹慎使用。

## 範例
### 基本用法
以下是使用 `ResizeObserver` 的基本範例：

```javascript
const box = document.getElementById('box');

const observer = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log(`Dimensions changed: ${entry.contentRect.width} x ${entry.contentRect.height}`);
    }
});

observer.observe(box);
```

### 停止監控
如果需要停止監控，可以這樣做：

```javascript
observer.unobserve(box); // 停止監控單個元素
observer.disconnect(); // 停止監控所有元素
```

## 說明
- **常見陷阱**：當元素的大小變化不明顯或頻繁時，可能會導致性能問題。建議限制觀察的元素數量，並在回調函數中進行適當的節流或防抖處理。
- **特定瀏覽器支援**：`ResizeObserver` 在現代瀏覽器中有良好的支援，但建議查看兼容性以確保在舊版瀏覽器上能夠正常運行。

## 總結
`ResizeObserver` 是一個強大的工具，能夠幫助開發者有效地監控元素的尺寸變化，並即時更新界面以提高用戶體驗。