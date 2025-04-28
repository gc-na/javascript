<!--
Meta Description: # WebGL2RenderingContext：JavaScript中的高效3D圖形渲染 ## 簡介 WebGL2RenderingContext是HTML5中的一個API，允許在網頁中實現高效的3D圖形渲染。它是WebGL的擴展版本，提供了更多的功能和更好的性能，適用於需要高性能圖形渲染的Web...
Meta Keywords: canvas, const, mycanvas, width, height
-->

# WebGL2RenderingContext：JavaScript中的高效3D圖形渲染

## 簡介
WebGL2RenderingContext是HTML5中的一個API，允許在網頁中實現高效的3D圖形渲染。它是WebGL的擴展版本，提供了更多的功能和更好的性能，適用於需要高性能圖形渲染的Web應用程式。

## 文檔
### 目的
WebGL2RenderingContext主要用於在網頁中渲染2D和3D圖形。它基於OpenGL ES 3.0，提供了更強大的圖形處理功能，並支持更多的圖形特性，如多重渲染目標、3D紋理及更高效的數據處理。

### 使用方法
要使用WebGL2RenderingContext，首先需要在HTML中創建一個canvas元素，然後通過JavaScript獲取其上下文。

### 詳細說明
以下是創建WebGL2RenderingContext的基本步驟：

1. **創建canvas元素**：
   ```html
   <canvas id="myCanvas" width="800" height="600"></canvas>
   ```

2. **獲取WebGL2上下文**：
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const gl = canvas.getContext('webgl2');
   if (!gl) {
       console.error('WebGL 2 not supported, falling back on WebGL 1');
   }
   ```

3. **設置視口**：
   ```javascript
   gl.viewport(0, 0, canvas.width, canvas.height);
   ```

4. **清除顏色和深度緩衝區**：
   ```javascript
   gl.clearColor(0.0, 0.0, 0.0, 1.0);
   gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT);
   ```

WebGL2RenderingContext還支持多種操作，如著色器程序的創建、頂點緩衝區的綁定和渲染調用等。

## 例子
### 基本用法範例
以下是一個簡單的WebGL2例子，用於在canvas中顯示一個紅色的三角形：

```html
<canvas id="myCanvas" width="800" height="600"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const gl = canvas.getContext('webgl2');
    
    const vertices = new Float32Array([
        0.0,  0.5, 0.0,
       -0.5, -0.5, 0.0,
        0.5, -0.5, 0.0,
    ]);

    const vertexBuffer = gl.createBuffer();
    gl.bindBuffer(gl.ARRAY_BUFFER, vertexBuffer);
    gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW);

    gl.clearColor(1.0, 0.0, 0.0, 1.0);
    gl.clear(gl.COLOR_BUFFER_BIT);
    
    gl.vertexAttribPointer(0, 3, gl.FLOAT, false, 0, 0);
    gl.enableVertexAttribArray(0);
    
    gl.drawArrays(gl.TRIANGLES, 0, 3);
</script>
```

## 解釋
### 常見問題
- **不支持的瀏覽器**：WebGL2不在所有瀏覽器上都支持，開發者需檢查用戶的瀏覽器兼容性。
- **上下文獲取失敗**：如果getContext('webgl2')返回null，可能是因為瀏覽器不支持WebGL2或者設備不符合要求。
- **性能考量**：使用WebGL2時，需注意性能優化，避免使用不必要的重繪或過多的渲染呼叫。

## 一句話總結
WebGL2RenderingContext是一個強大的JavaScript API，用於在網頁中實現高效的3D圖形渲染，支持多種高級圖形特性。