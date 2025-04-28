<!--
Meta Description: # DataTransfer: JavaScript 中的數據傳輸接口 ## 概述 `DataTransfer` 是一個 JavaScript 接口，用於管理拖放操作中的數據傳輸，特別是在使用 HTML5 拖放 API 時。它提供了一個統一的方式來訪問和操作拖放過程中的數據。 ## 文檔 `Data...
Meta Keywords: datatransfer, event, javascript, drop, dragover
-->

# DataTransfer: JavaScript 中的數據傳輸接口

## 概述
`DataTransfer` 是一個 JavaScript 接口，用於管理拖放操作中的數據傳輸，特別是在使用 HTML5 拖放 API 時。它提供了一個統一的方式來訪問和操作拖放過程中的數據。

## 文檔
`DataTransfer` 接口的主要目的是在拖放操作中，允許開發者存儲和檢索要傳輸的數據。這個接口的實例通常是在拖放事件（如 `dragstart`、`dragover` 和 `drop` 事件）中自動創建的，它包含以下重要屬性和方法：

### 主要屬性
- **dataTransfer.effectAllowed**: 定義拖放操作的效果，例如 "copy", "move", "link"。
- **dataTransfer.dropEffect**: 定義放置操作的效果，常用值包括 "copy", "move", "none"。
- **dataTransfer.items**: 一個 `DataTransferItemList` 對象，代表正在傳輸的項目。
- **dataTransfer.setData(format, data)**: 設定指定格式的數據。
- **dataTransfer.getData(format)**: 獲取指定格式的數據。
- **dataTransfer.clearData(format)**: 清除指定格式的數據。

### 使用方法
在實現拖放功能時，通常需要在以下事件中使用 `DataTransfer`：
1. `dragstart`: 在拖動開始時設置要傳輸的數據。
2. `dragover`: 在元素上拖動時，通常需要阻止默認行為以允許放置。
3. `drop`: 在目標元素上放置時獲取傳輸的數據。

## 範例
以下是一個簡單的拖放示例，演示如何使用 `DataTransfer`：

```javascript
// HTML 部分
<div id="drag-source" draggable="true">拖動我</div>
<div id="drop-target">放置區域</div>

// JavaScript 部分
const dragSource = document.getElementById('drag-source');
const dropTarget = document.getElementById('drop-target');

dragSource.addEventListener('dragstart', (event) => {
    event.dataTransfer.setData('text/plain', '這是拖動的數據');
});

dropTarget.addEventListener('dragover', (event) => {
    event.preventDefault(); // 允許放置
});

dropTarget.addEventListener('drop', (event) => {
    event.preventDefault(); // 防止默認行為
    const data = event.dataTransfer.getData('text/plain');
    alert(`放置的數據: ${data}`);
});
```

## 解釋
在使用 `DataTransfer` 時，開發者應注意以下幾點：
- **安全性**: 確保不在不安全的上下文中使用拖放，以避免資料洩露。
- **格式一致性**: 使用 `setData` 和 `getData` 時，確保格式一致，以防獲取不到數據。
- **事件阻止**: 在 `dragover` 事件中，必須調用 `event.preventDefault()` 來允許放置，否則放置事件將不會被觸發。

## 一句總結
`DataTransfer` 是 JavaScript 用於處理拖放操作中數據傳輸的關鍵接口，允許開發者輕鬆地設置和獲取拖動的數據。