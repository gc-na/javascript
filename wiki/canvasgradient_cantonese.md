<!--
Meta Description: # CanvasGradient：JavaScript 中的漸變對象 ## 概述 CanvasGradient 是一個用於創建漸變顏色的對象，主要用於 HTML5 的 Canvas API。它允許開發者在畫布上生成平滑的顏色過渡，增強圖形的視覺效果。 ## 文檔 CanvasGradient 主要用...
Meta Keywords: ctx, gradient, canvas, canvasgradient, const
-->

# CanvasGradient：JavaScript 中的漸變對象

## 概述
CanvasGradient 是一個用於創建漸變顏色的對象，主要用於 HTML5 的 Canvas API。它允許開發者在畫布上生成平滑的顏色過渡，增強圖形的視覺效果。

## 文檔
CanvasGradient 主要用於定義線性或放射狀漸變色。通過使用 `createLinearGradient` 或 `createRadialGradient` 方法，開發者可以創建不同的漸變效果。

### 目的
CanvasGradient 的主要目的是為了提供一種簡單的方式來創建顏色漸變，使得圖形的填充和描邊具有更高的視覺吸引力。

### 使用
1. **創建一個 Canvas 類型的上下文**：
   使用 `getContext('2d')` 方法來獲取 2D 渲染上下文。
   
2. **創建漸變對象**：
   - **線性漸變**：使用 `createLinearGradient(x0, y0, x1, y1)` 方法來定義漸變的起始和結束點。
   - **放射狀漸變**：使用 `createRadialGradient(x0, y0, r0, x1, y1, r1)` 方法來定義漸變的圓心和半徑。

3. **添加顏色停點**：
   使用 `addColorStop(offset, color)` 方法，可以在漸變中添加顏色停點，`offset` 為 0 到 1 之間的值，表示顏色的相對位置。

### 詳細信息
- 漸變對象可以在填充或描邊時使用，透過 `fillStyle` 或 `strokeStyle` 屬性來指定。
- 漸變顏色的設置必須在繪製圖形之前完成。

## 範例
### 線性漸變範例
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

const gradient = ctx.createLinearGradient(0, 0, 200, 0);
gradient.addColorStop(0, 'red');
gradient.addColorStop(1, 'blue');

ctx.fillStyle = gradient;
ctx.fillRect(10, 10, 200, 100);
```

### 放射狀漸變範例
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

const gradient = ctx.createRadialGradient(150, 70, 20, 150, 70, 100);
gradient.addColorStop(0, 'yellow');
gradient.addColorStop(1, 'green');

ctx.fillStyle = gradient;
ctx.fillRect(10, 10, 200, 200);
```

## 解釋
在使用 CanvasGradient 時，開發者應注意以下幾點：
- 確保顏色停點的 `offset` 值在 0 到 1 之間，否則可能會導致錯誤的顏色顯示。
- 漸變效果在高解析度畫布上可能會顯得更加平滑。
- 不同的瀏覽器對於顏色的渲染可能會有細微差異，因此在不同環境中測試非常重要。

## 一句總結
CanvasGradient 是一個用於在 HTML5 Canvas 中創建平滑顏色漸變的對象，使得圖形更加生動。