<!--
Meta Description: # WebGLRenderingContext：JavaScript 中的高效圖形渲染上下文 ## 概要 WebGLRenderingContext 是一個在 JavaScript 中使用的介面，允許開發者在網頁上進行高性能的 3D 圖形渲染。它基於 OpenGL ES 2.0，透過 HTML5 的...
Meta Keywords: webgl, canvas, webglrenderingcontext, var, javascript
-->

# WebGLRenderingContext：JavaScript 中的高效圖形渲染上下文

## 概要
WebGLRenderingContext 是一個在 JavaScript 中使用的介面，允許開發者在網頁上進行高性能的 3D 圖形渲染。它基於 OpenGL ES 2.0，透過 HTML5 的 `<canvas>` 元素提供硬體加速的圖形顯示。

## 文檔
### 目的
WebGLRenderingContext 主要用於在瀏覽器中進行 3D 圖形的渲染，支持著色器、頂點緩衝區和紋理等技術，讓開發者能夠創建豐富的視覺效果和互動式應用。

### 使用方法
要使用 WebGLRenderingContext，首先需要在 HTML 文件中創建一個 `<canvas>` 元素，然後通過 JavaScript 獲取其上下文。以下是基本的步驟：

```html
<canvas id="myCanvas" width="800" height="600"></canvas>
<script>
    var canvas = document.getElementById('myCanvas');
    var gl = canvas.getContext('webgl');

    if (!gl) {
        console.error('WebGL not supported, falling back on experimental-webgl');
        gl = canvas.getContext('experimental-webgl');
    }

    if (!gl) {
        alert('Your browser does not support WebGL');
    }
</script>
```

### 詳細說明
- **上下文獲取**：使用 `canvas.getContext('webgl')` 獲取 WebGLRenderingContext，這是進行所有 WebGL 操作的基礎。
- **著色器**：WebGL 使用 GLSL（OpenGL Shading Language）來編寫著色器，著色器負責計算每個像素的顏色和其他屬性。
- **緩衝區**：開發者可以創建頂點緩衝區（Vertex Buffer）和索引緩衝區（Index Buffer），用於儲存模型的幾何數據。
- **繪製命令**：使用 `gl.drawArrays()` 或 `gl.drawElements()` 來繪製物體。

## 範例
### 基本使用範例
以下是簡單的範例，展示如何使用 WebGLRenderingContext 繪製一個彩色的三角形。

```javascript
var vertices = new Float32Array([
    0.0,  1.0,
   -1.0, -1.0,
    1.0, -1.0,
]);

var vertexBuffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, vertexBuffer);
gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW);

var vertexShaderSource = `
    attribute vec2 coordinates;
    void main(void) {
        gl_Position = vec4(coordinates, 0.0, 1.0);
    }`;

var fragmentShaderSource = `
    void main(void) {
        gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0);
    }`;

// Compile shaders and link program (省略編譯與鏈接代碼)

gl.clearColor(0.0, 0.0, 0.0, 1.0);
gl.clear(gl.COLOR_BUFFER_BIT);
gl.vertexAttribPointer(0, 2, gl.FLOAT, false, 0, 0);
gl.enableVertexAttribArray(0);

gl.drawArrays(gl.TRIANGLES, 0, 3);
```

## 解釋
- **支援性**：確保檢查瀏覽器是否支持 WebGL，某些舊的或不兼容的瀏覽器可能無法運行 WebGL。
- **性能**：使用緩衝區和著色器可以大幅提高渲染效率，避免每幀都重新傳輸數據。
- **跨域問題**：從不同域名載入圖像或資源時，可能會遇到 CORS（跨來源資源共享）問題，確保正確設置 HTTP 標頭。

## 一句總結
WebGLRenderingContext 是 JavaScript 中一個強大的介面，用於實現高性能的 3D 圖形渲染，適用於網頁應用和遊戲開發。