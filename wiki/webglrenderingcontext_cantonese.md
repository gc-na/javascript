<!--
Meta Description: # WebGLRenderingContext：JavaScript 中的網頁圖形渲染上下文 ## 簡介 WebGLRenderingContext 是一個提供在網頁上進行 3D 渲染的 API，允許開發者利用 GPU 加速來生成高效的圖形效果。 ## 文檔 WebGLRenderingContex...
Meta Keywords: canvas, webglrenderingcontext, const, webgl, javascript
-->

# WebGLRenderingContext：JavaScript 中的網頁圖形渲染上下文

## 簡介
WebGLRenderingContext 是一個提供在網頁上進行 3D 渲染的 API，允許開發者利用 GPU 加速來生成高效的圖形效果。

## 文檔
WebGLRenderingContext 是 WebGL API 的主要組件，主要用於從 HTML5 的 `<canvas>` 元素中創建 3D 圖形。它提供了一系列的函數和屬性來控制圖形的渲染過程，包括著色器的編譯、幾何圖形的繪製和紋理的應用。

### 主要功能
- **初始化**：通過 `getContext('webgl')` 獲取 WebGLRenderingContext 實例。
- **著色器**：支持頂點著色器和片段著色器的創建與使用。
- **紋理管理**：可以處理各種紋理，包括圖像紋理和立方體紋理。
- **幾何圖形繪製**：支持多種繪製方式，如點、線和三角形。

### 使用方法
首先，需在 HTML 中創建一個 `<canvas>` 元素，然後使用 JavaScript 獲取 WebGLRenderingContext：
```html
<canvas id="myCanvas" width="500" height="500"></canvas>
<script>
  const canvas = document.getElementById('myCanvas');
  const gl = canvas.getContext('webgl');
</script>
```
接著，可以使用 `gl` 對象來執行各種渲染操作。

## 示例
### 基本示例
以下是創建一個簡單紅色三角形的示例：
```javascript
const canvas = document.getElementById('myCanvas');
const gl = canvas.getContext('webgl');

// 定義三角形的頂點
const vertices = new Float32Array([
  0.0,  1.0,
 -1.0, -1.0,
  1.0, -1.0,
]);

// 創建緩衝區
const vertexBuffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, vertexBuffer);
gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW);

// 進行繪製
gl.clearColor(1.0, 1.0, 1.0, 1.0); // 設定背景色為白色
gl.clear(gl.COLOR_BUFFER_BIT);

gl.vertexAttribPointer(0, 2, gl.FLOAT, false, 0, 0);
gl.enableVertexAttribArray(0);
gl.drawArrays(gl.TRIANGLES, 0, 3);
```

## 解釋
使用 WebGLRenderingContext 時，開發者常會遇到以下問題：
- **上下文丟失**：如果 GPU 資源不足，WebGL 上下文可能會丟失，需定期檢查。
- **著色器錯誤**：著色器編譯失敗時，需檢查語法錯誤或不支持的特性。
- **性能問題**：不當使用緩衝區或著色器可能導致性能下降，需謹慎選擇。

## 一句總結
WebGLRenderingContext 使得開發者可以在網頁上高效地進行 3D 圖形渲染。