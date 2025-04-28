<!--
Meta Description: # CanvasRenderingContext2D：JavaScript 的 2D 畫布渲染上下文 ## 簡介 CanvasRenderingContext2D 是一個用於在 HTML5 canvas 元素上進行 2D 繪圖的 JavaScript 接口。它提供了一組方法和屬性，允許開發者進行形狀...
Meta Keywords: canvas, ctx, canvasrenderingcontext2d, const, javascript
-->

# CanvasRenderingContext2D：JavaScript 的 2D 畫布渲染上下文

## 簡介
CanvasRenderingContext2D 是一個用於在 HTML5 canvas 元素上進行 2D 繪圖的 JavaScript 接口。它提供了一組方法和屬性，允許開發者進行形狀繪製、影像處理、文本顯示等操作。

## 文檔
CanvasRenderingContext2D 的主要目的是提供一個可操作的 2D 繪圖環境，開發者可以通過它來創建豐富的圖形和動畫。要使用 CanvasRenderingContext2D，首先需要獲取 canvas 元素的上下文，通常通過以下方法：

```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
```

### 主要功能
- **繪製形狀**：提供如 `fillRect()`、`strokeRect()`、`beginPath()` 等方法用於繪製矩形、圓形及其他形狀。
- **顏色及樣式**：可設置填充顏色、邊框顏色和樣式，例如使用 `fillStyle` 和 `strokeStyle` 屬性。
- **文本處理**：可使用 `fillText()` 和 `strokeText()` 方法在畫布上繪製文本。
- **影像處理**：可使用 `drawImage()` 方法將圖像繪製到畫布上。
- **變換**：支持變換功能，如旋轉、縮放和平移，通過 `translate()`、`rotate()` 和 `scale()` 方法實現。

## 示例
### 基本使用範例
```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
  const canvas = document.getElementById('myCanvas');
  const ctx = canvas.getContext('2d');

  // 繪製矩形
  ctx.fillStyle = '#FF0000';
  ctx.fillRect(20, 20, 150, 100);

  // 繪製圓形
  ctx.beginPath();
  ctx.arc(240, 70, 50, 0, Math.PI * 2, false);
  ctx.fillStyle = 'blue';
  ctx.fill();
  ctx.stroke();
</script>
```

## 解釋
### 常見陷阱和注意事項
- **畫布大小**：確保設定 canvas 的寬度和高度，否則可能導致畫面顯示不正確。
- **坐標系統**：畫布的坐標系統以左上角為原點，x 軸向右，y 軸向下。
- **抗鋸齒**：某些繪製操作可能會受到抗鋸齒的影響，特別是在縮放圖形時，應注意這一點。
- **上下文狀態**：每次繪製之前，最好使用 `beginPath()` 方法來清除之前的路徑，以避免不必要的繪圖錯誤。

## 一句總結
CanvasRenderingContext2D 是用於在 HTML5 canvas 上進行 2D 繪圖的強大工具，提供了多種方法來創建各種圖形和效果。