<!--
Meta Description: # OffscreenCanvas：JavaScript 的離屏畫布技術 ## 概述 `OffscreenCanvas` 是一個 JavaScript API，允許在主執行緒之外進行畫布的繪製操作，這對於提高性能和效率特別有用，特別是在處理大量圖形或動畫時。 ## 文檔 ### 目的 `Offscr...
Meta Keywords: offscreencanvas, const, worker, offscreen, javascript
-->

# OffscreenCanvas：JavaScript 的離屏畫布技術

## 概述
`OffscreenCanvas` 是一個 JavaScript API，允許在主執行緒之外進行畫布的繪製操作，這對於提高性能和效率特別有用，特別是在處理大量圖形或動畫時。

## 文檔
### 目的
`OffscreenCanvas` 的主要目的是提供一個可在 Web 工作執行緒中使用的畫布，從而減少主執行緒的負擔，實現更流暢的用戶體驗。

### 使用方法
要創建一個 `OffscreenCanvas`，您可以使用以下語法：

```javascript
const offscreen = new OffscreenCanvas(width, height);
```

這裡的 `width` 和 `height` 分別表示畫布的寬度和高度。

#### 主要功能
- **繪製圖形**：可以使用 `2D` 或 `WebGL` 上下文進行圖形繪製。
- **離屏渲染**：允許在 Web Worker 中進行渲染，減少主執行緒的負擔。
- **圖像處理**：可用於圖像處理和動態生成圖像。

### 詳細說明
`OffscreenCanvas` 的使用需要注意以下幾點：
1. **上下文獲取**：通過 `getContext()` 方法獲取繪圖上下文。
2. **與主畫布同步**：可以通過 `transferToImageBitmap()` 方法將離屏畫布的內容轉移到主畫布中。
3. **Web Worker 支持**：`OffscreenCanvas` 可以在 Web Worker 中使用，這使得進行重計算和渲染的操作不會阻塞主線程。

## 範例
以下是一些基本的使用範例：

### 範例 1：基本的 OffscreenCanvas 使用
```javascript
const offscreen = new OffscreenCanvas(300, 150);
const ctx = offscreen.getContext('2d');

ctx.fillStyle = 'blue';
ctx.fillRect(0, 0, 300, 150);

// 將圖像轉移到主畫布
const bitmap = offscreen.transferToImageBitmap();
const mainCanvas = document.getElementById('mainCanvas');
const mainCtx = mainCanvas.getContext('2d');
mainCtx.drawImage(bitmap, 0, 0);
```

### 範例 2：在 Web Worker 中使用 OffscreenCanvas
```javascript
// worker.js
self.onmessage = function(e) {
    const offscreen = new OffscreenCanvas(300, 150);
    const ctx = offscreen.getContext('2d');

    ctx.fillStyle = 'red';
    ctx.fillRect(0, 0, 300, 150);

    const bitmap = offscreen.transferToImageBitmap();
    self.postMessage(bitmap);
};

// main.js
const worker = new Worker('worker.js');
worker.onmessage = function(e) {
    const bitmap = e.data;
    const mainCanvas = document.getElementById('mainCanvas');
    const mainCtx = mainCanvas.getContext('2d');
    mainCtx.drawImage(bitmap, 0, 0);
};

worker.postMessage();
```

## 解釋
在使用 `OffscreenCanvas` 時，開發者需注意以下幾個常見問題：
- **不支援的瀏覽器**：並非所有瀏覽器都支持 `OffscreenCanvas`，因此需要檢查兼容性。
- **性能考量**：雖然 `OffscreenCanvas` 提升了性能，但過度使用仍可能導致性能下降，需謹慎使用。
- **資源管理**：在 Web Worker 中使用時，需妥善管理畫布資源，以避免內存泄漏。

## 總結
`OffscreenCanvas` 是一個強大的工具，能有效提升 JavaScript 中的圖形處理性能，特別適合需要高效渲染的應用。