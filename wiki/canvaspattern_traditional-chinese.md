<!--
Meta Description: # JavaScript 中的 CanvasPattern：全面解析與使用示例 ## 概述 CanvasPattern 是一個在 HTML5 Canvas API 中使用的對象，允許開發者創建可重複的圖案以用於填充圖形或形狀。通過使用 CanvasPattern，開發者可以將圖像或其他畫布內容應用於...
Meta Keywords: canvas, repeat, const, ctx, img
-->

# JavaScript 中的 CanvasPattern：全面解析與使用示例

## 概述
CanvasPattern 是一個在 HTML5 Canvas API 中使用的對象，允許開發者創建可重複的圖案以用於填充圖形或形狀。通過使用 CanvasPattern，開發者可以將圖像或其他畫布內容應用於繪圖，提供了更高的可視化效果。

## 文檔
CanvasPattern 的主要目的是為了創建可重複的圖案填充。開發者可以使用 `createPattern()` 方法來生成 CanvasPattern 對象。這個對象可以用於設置填充樣式，並可用於各種繪圖操作，例如矩形、圓形等的填充。

### 用法
1. **創建畫布**：首先，創建一個 `<canvas>` 元素並獲取其上下文。
2. **加載圖像**：使用 `Image` 對象或其他方法加載要用作圖案的圖片。
3. **創建圖案**：使用 `context.createPattern(image, repetition)` 方法創建 CanvasPattern。
   - `image`：要用作圖案的圖像對象。
   - `repetition`：是一個字符串，定義了圖案的重複方式，可以是 `repeat`、`repeat-x`、`repeat-y` 或 `no-repeat`。
4. **使用圖案填充**：將創建的圖案應用到填充樣式中，然後繪製圖形。

### 詳細步驟
```javascript
// 獲取畫布上下文
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// 創建圖像對象
const img = new Image();
img.src = 'path/to/image.png'; // 圖像路徑

img.onload = function() {
    // 創建圖案
    const pattern = ctx.createPattern(img, 'repeat');
    
    // 設置填充樣式為圖案
    ctx.fillStyle = pattern;
    
    // 繪製矩形
    ctx.fillRect(0, 0, canvas.width, canvas.height);
};
```

## 示例
### 基本使用示例
```html
<canvas id="myCanvas" width="500" height="500"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');
    const img = new Image();

    img.src = 'https://example.com/pattern.png'; // 圖案圖片 URL
    img.onload = function() {
        const pattern = ctx.createPattern(img, 'repeat');
        ctx.fillStyle = pattern;
        ctx.fillRect(0, 0, 500, 500); // 用圖案填充整個畫布
    };
</script>
```

## 解釋
### 常見問題與注意事項
1. **圖像未加載**：確保在圖像加載完成後再創建圖案，否則可能會導致圖案為 `null`。
2. **圖案尺寸**：注意圖案的尺寸會影響到填充效果，較大的圖案可能會導致性能問題。
3. **重複模式**：選擇合適的重複模式（`repeat`、`repeat-x`、`repeat-y`、`no-repeat`）對於達到理想的視覺效果至關重要。

## 一句話總結
CanvasPattern 是一種用於在 HTML5 Canvas 中創建可重複圖案填充的對象，使得圖形繪製更具創意和美觀。