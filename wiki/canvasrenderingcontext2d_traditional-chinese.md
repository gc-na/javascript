<!--
Meta Description: # CanvasRenderingContext2D：JavaScript 中的 2D 畫布渲染上下文 ## 概述 `CanvasRenderingContext2D` 是一個用於在 HTML5 `<canvas>` 元素上進行 2D 繪圖的接口。它提供了一系列方法和屬性，使開發者能夠在畫布上繪製圖...
Meta Keywords: ctx, canvas, canvasrenderingcontext2d, const, javascript
-->

# CanvasRenderingContext2D：JavaScript 中的 2D 畫布渲染上下文

## 概述
`CanvasRenderingContext2D` 是一個用於在 HTML5 `<canvas>` 元素上進行 2D 繪圖的接口。它提供了一系列方法和屬性，使開發者能夠在畫布上繪製圖形、文本和影像。

## 文檔
`CanvasRenderingContext2D` 的主要目的是為了提供 API 來操作和渲染 2D 圖形。當使用 `<canvas>` 元素時，開發者可以獲取其渲染上下文，然後使用該上下文的各種方法來繪製內容。

### 使用方法
1. **獲取 Canvas 元素**：
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   ```

2. **基本繪圖**：
   - **畫直線**：
     ```javascript
     ctx.beginPath();
     ctx.moveTo(50, 50);
     ctx.lineTo(200, 50);
     ctx.stroke();
     ```

   - **畫矩形**：
     ```javascript
     ctx.fillStyle = '#FF0000';
     ctx.fillRect(20, 20, 150, 100);
     ```

   - **畫圓形**：
     ```javascript
     ctx.beginPath();
     ctx.arc(100, 100, 50, 0, Math.PI * 2);
     ctx.fillStyle = '#00FF00';
     ctx.fill();
     ```

### 詳細說明
`CanvasRenderingContext2D` 包含多種方法，如 `fillRect()`、`strokeRect()`、`clearRect()`、`beginPath()`、`arc()` 等，這些方法可以用來實現複雜的圖形效果。開發者可以控制顏色、線條樣式、陰影等屬性，實現高度自定義的繪圖效果。

## 範例
### 基本範例：畫一個藍色矩形
```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');

   ctx.fillStyle = '#0000FF';
   ctx.fillRect(50, 50, 200, 100);
</script>
```

### 繪製圓形與文字
```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');

   ctx.fillStyle = '#FF0000';
   ctx.beginPath();
   ctx.arc(200, 200, 50, 0, Math.PI * 2);
   ctx.fill();

   ctx.font = '20px Arial';
   ctx.fillStyle = '#000000';
   ctx.fillText('Hello, Canvas!', 150, 250);
</script>
```

## 解釋
在使用 `CanvasRenderingContext2D` 時，開發者需要注意：

- **畫布大小**：設定 `<canvas>` 的寬度和高度時，必須在 HTML 中直接指定，否則可能導致縮放問題。
- **坐標系**：畫布的坐標系原點在左上角，X 軸向右延伸，Y 軸向下延伸。
- **性能考量**：大量繪圖操作可能影響性能，建議在單一繪圖操作中進行多個繪圖命令的組合。

## 一句總結
`CanvasRenderingContext2D` 是一個強大的 API，使開發者能夠在 HTML5 Canvas 上進行高效、美觀的 2D 繪圖。