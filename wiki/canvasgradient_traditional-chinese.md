<!--
Meta Description: # CanvasGradient：JavaScript 中的漸層效果 ## 簡介 CanvasGradient 是 JavaScript 中用於在 HTML5 Canvas 上創建漸層效果的對象。它允許開發者使用線性或放射性漸層填充形狀，增強視覺效果，並改善用戶界面。 ## 文檔 ### 目的 Ca...
Meta Keywords: canvas, ctx, const, addcolorstop, javascript
-->

# CanvasGradient：JavaScript 中的漸層效果

## 簡介
CanvasGradient 是 JavaScript 中用於在 HTML5 Canvas 上創建漸層效果的對象。它允許開發者使用線性或放射性漸層填充形狀，增強視覺效果，並改善用戶界面。

## 文檔
### 目的
CanvasGradient 的主要目的是提供一種簡單的方法來在 Canvas 上創建漸層效果，這使得開發者能夠在圖形和圖像中添加深度和動感。

### 使用方法
1. **創建 Canvas 和上下文**：
   使用 `getContext('2d')` 方法獲取 Canvas 的 2D 上下文。
   
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   ```

2. **創建漸層**：
   使用 `createLinearGradient(x0, y0, x1, y1)` 或 `createRadialGradient(x0, y0, r0, x1, y1, r1)` 方法來創建漸層對象。
   
   ```javascript
   // 線性漸層
   const linearGradient = ctx.createLinearGradient(0, 0, 200, 0);
   linearGradient.addColorStop(0, 'red');
   linearGradient.addColorStop(1, 'blue');
   
   // 放射性漸層
   const radialGradient = ctx.createRadialGradient(100, 100, 50, 100, 100, 100);
   radialGradient.addColorStop(0, 'yellow');
   radialGradient.addColorStop(1, 'green');
   ```

3. **填充形狀**：
   將漸層對象應用於填充，例如矩形或圓形。
   
   ```javascript
   // 使用線性漸層填充矩形
   ctx.fillStyle = linearGradient;
   ctx.fillRect(10, 10, 200, 100);
   
   // 使用放射性漸層填充圓形
   ctx.fillStyle = radialGradient;
   ctx.beginPath();
   ctx.arc(150, 150, 50, 0, Math.PI * 2);
   ctx.fill();
   ```

### 詳細說明
- `addColorStop(offset, color)`：用於定義漸層中的顏色停點。`offset` 是一個 0 到 1 的值，表示顏色在漸層中的位置。
- 漸層可以用於各種形狀填充，包括矩形、圓形和路徑。
- 漸層的顏色可以是十六進制、RGB 或 RGBA 格式。

## 範例
以下是一個基本的範例，展示如何在 Canvas 上使用 CanvasGradient 創建漸層效果。

```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');

   // 創建線性漸層
   const gradient = ctx.createLinearGradient(0, 0, 400, 0);
   gradient.addColorStop(0, 'blue');
   gradient.addColorStop(1, 'red');

   // 使用漸層填充矩形
   ctx.fillStyle = gradient;
   ctx.fillRect(0, 0, 400, 200);
</script>
```

## 解釋
- **常見陷阱**：確保在創建漸層之前，Canvas 上下文已正確獲取。
- **漸層的顏色停點**：如果使用的 `offset` 值不在 0 到 1 的範圍內，漸層將無法正常顯示。
- **不支持的顏色格式**：使用不正確的顏色格式將導致漸層無法渲染。

## 一句總結
CanvasGradient 是 JavaScript 中用於在 HTML5 Canvas 上創建豐富漸層效果的強大工具。