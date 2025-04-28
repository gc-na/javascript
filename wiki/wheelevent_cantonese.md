<!--
Meta Description: # WheelEvent：JavaScript 中的滑鼠滾輪事件 ## 概述 `WheelEvent` 是一種在 JavaScript 中用於處理滑鼠滾輪事件的事件類型。它可用於偵測用戶的滑鼠滾輪動作，進而觸發相應的功能，比如滾動頁面或縮放內容。 ## 文件說明 `WheelEvent` 主要用於捕...
Meta Keywords: wheelevent, event, javascript, addeventlistener, deltax
-->

# WheelEvent：JavaScript 中的滑鼠滾輪事件

## 概述
`WheelEvent` 是一種在 JavaScript 中用於處理滑鼠滾輪事件的事件類型。它可用於偵測用戶的滑鼠滾輪動作，進而觸發相應的功能，比如滾動頁面或縮放內容。

## 文件說明
`WheelEvent` 主要用於捕捉使用者的滾輪行為。當用戶滾動滑鼠滾輪時，瀏覽器會生成一個 `WheelEvent` 事件，開發者可以通過事件監聽器來捕捉這些事件並執行相應的操作。

### 目的
- 監控滑鼠滾輪的運動。
- 提供滾動的方向與速度資訊。
- 支持多種設備，包括觸控板和觸控裝置。

### 用法
`WheelEvent` 事件通常在 DOM 元素上註冊，並使用 `addEventListener` 方法來監聽。例如：

```javascript
element.addEventListener('wheel', function(event) {
    // 事件處理邏輯
});
```

### 事件屬性
- `deltaX`：水平滾動的距離。
- `deltaY`：垂直滾動的距離。
- `deltaZ`：三維滾動的距離（通常為 0）。
- `deltaMode`：滾動單位的模式，可以是像素、行或頁面。

## 示例
以下是一個簡單的使用範例，展示如何使用 `WheelEvent` 來檢測滾動：

```javascript
const box = document.getElementById('scrollable-box');

box.addEventListener('wheel', function(event) {
    // 防止默認滾動行為
    event.preventDefault();

    // 顯示滾動的距離
    console.log(`deltaX: ${event.deltaX}, deltaY: ${event.deltaY}`);
});
```

在這個範例中，我們創建了一個可滾動的區域，並在用戶滾動時記錄滾動的距離。

## 解釋
在使用 `WheelEvent` 時，有一些常見的陷阱需要注意：

- **事件的默認行為**：如果不調用 `event.preventDefault()`，頁面可能會因為滾動而移動。
- **滾動速度**：不同的設備和瀏覽器可能會對滾輪的靈敏度進行不同的處理，這可能會導致滾動速度的差異。
- **跨瀏覽器的兼容性**：雖然大多數現代瀏覽器都支持 `WheelEvent`，但仍建議進行測試以確保功能在所有目標瀏覽器中正常運作。

## 總結
`WheelEvent` 是 JavaScript 中用於捕捉滑鼠滾輪事件的強大工具，能夠提供豐富的滾動資訊，幫助開發者創建更具互動性的網站和應用程式。