<!--
Meta Description: # CanvasPattern：JavaScript 中的圖案填充 ## 簡介 CanvasPattern 是一個用於 HTML5 Canvas API 的物件，允許開發者在 Canvas 上創建可重複的圖案填充，以製作複雜的視覺效果。 ## 文檔 CanvasPattern 主要用於在 Canva...
Meta Keywords: canvas, img, const, ctx, pattern
-->

# CanvasPattern：JavaScript 中的圖案填充

## 簡介
CanvasPattern 是一個用於 HTML5 Canvas API 的物件，允許開發者在 Canvas 上創建可重複的圖案填充，以製作複雜的視覺效果。

## 文檔
CanvasPattern 主要用於在 Canvas 元素上應用圖案填充。這種圖案可以是任何圖像或 Canvas 物件，並且可以自定義其重複方式。使用 CanvasPattern，可以輕鬆地在圖形上添加紋理或背景，提升視覺吸引力。

### 使用方法
要創建一個 CanvasPattern，首先需要獲取一個 CanvasRenderingContext2D 物件，然後使用 `createPattern()` 方法。該方法接受兩個參數：圖像或 Canvas 物件，以及圖案的重複模式（如 `"repeat"`、`"repeat-x"`、`"repeat-y"` 或 `"no-repeat"`）。

### 詳細說明
```javascript
// 獲取 Canvas 元素及其上下文
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// 創建圖像物件
const img = new Image();
img.src = 'path/to/image.png'; // 替換為您的圖像路徑

// 當圖像加載完成後創建圖案
img.onload = function() {
    const pattern = ctx.createPattern(img, 'repeat');
    ctx.fillStyle = pattern; // 設置填充樣式為圖案
    ctx.fillRect(0, 0, canvas.width, canvas.height); // 填充整個畫布
};
```

## 範例
1. **基本圖案填充**
   ```javascript
   const canvas = document.getElementById('canvas');
   const ctx = canvas.getContext('2d');
   const img = new Image();
   img.src = 'pattern-image.png';
   img.onload = function() {
       const pattern = ctx.createPattern(img, 'repeat');
       ctx.fillStyle = pattern;
       ctx.fillRect(0, 0, canvas.width, canvas.height);
   };
   ```

2. **使用不重複的圖案**
   ```javascript
   const canvas = document.getElementById('canvas');
   const ctx = canvas.getContext('2d');
   const img = new Image();
   img.src = 'pattern-image.png';
   img.onload = function() {
       const pattern = ctx.createPattern(img, 'no-repeat');
       ctx.fillStyle = pattern;
       ctx.fillRect(50, 50, img.width, img.height); // 在特定位置繪製圖案
   };
   ```

## 解釋
使用 CanvasPattern 時，開發者需要注意以下幾點：

- **圖像加載**：在圖像未加載完成之前，不應使用 `createPattern()`，否則會導致圖案為 null。
- **性能考量**：重複圖案的性能可能會受到圖像大小影響，對於大型圖像，應考慮使用較小的圖像以提高性能。
- **支持性**：確保在使用的瀏覽器中支持 HTML5 Canvas API，較舊的瀏覽器可能不支持此功能。

## 總結
CanvasPattern 是一種強大的工具，能夠在 HTML5 Canvas 上創建多樣的圖案效果，增強視覺呈現。