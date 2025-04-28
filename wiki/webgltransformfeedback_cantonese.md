<!--
Meta Description: # WebGLTransformFeedback：JavaScript 中的 WebGL 轉換回饋 ## 概要 WebGLTransformFeedback 是一個在 WebGL 中用於實現圖形程序的轉換回饋（Transform Feedback）功能的 API，允許開發者捕獲著色器的輸出，並將其用...
Meta Keywords: webgl, webgltransformfeedback, const, begintransformfeedback, endtransformfeedback
-->

# WebGLTransformFeedback：JavaScript 中的 WebGL 轉換回饋

## 概要
WebGLTransformFeedback 是一個在 WebGL 中用於實現圖形程序的轉換回饋（Transform Feedback）功能的 API，允許開發者捕獲著色器的輸出，並將其用於後續的渲染或計算。

## 文檔
### 目的
WebGLTransformFeedback 的主要目的是提供一種方式來捕獲幾何圖形在著色器中的變換過程，並將這些數據存儲到緩衝區中。這允許開發者在不需要重新計算的情況下重用數據，從而提高性能。

### 使用
要使用 WebGLTransformFeedback，您首先需要創建一個 WebGL 上下文並設置必要的緩衝區和著色器程序。然後，可以使用 `gl.beginTransformFeedback()` 和 `gl.endTransformFeedback()` 方法來開始和結束轉換回饋過程。這兩個方法之間的所有渲染調用都會捕獲著色器的輸出。

### 詳細信息
1. **創建緩衝區**：使用 `gl.createBuffer()` 創建一個緩衝區來存儲轉換回饋的數據。
2. **設置著色器**：確保著色器程序能夠正確輸出數據到緩衝區，通常這需要使用 `out` 陳述來指定輸出變量。
3. **開始轉換回饋**：調用 `gl.beginTransformFeedback(primitiveType)`，其中 `primitiveType` 可以是 `gl.POINTS`、`gl.LINES` 或 `gl.TRIANGLES`。
4. **繪製**：執行繪製操作，如 `gl.drawArrays()`，以觸發著色器的執行並捕獲數據。
5. **結束轉換回饋**：使用 `gl.endTransformFeedback()` 結束過程。

## 示例
### 基本用法
```javascript
// 創建 WebGL 上下文
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl');

// 創建緩衝區
const buffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, buffer);

// 設置著色器
const vertexShaderSource = `
  #version 300 es
  precision mediump float;
  in vec4 position;
  out vec4 outputData;
  
  void main() {
    gl_Position = position;
    outputData = position; // 將位置作為輸出
  }
`;

const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

// 開始轉換回饋
gl.beginTransformFeedback(gl.TRIANGLES);
gl.drawArrays(gl.TRIANGLES, 0, 3);
gl.endTransformFeedback();
```

## 解釋
使用 WebGLTransformFeedback 時，有幾個常見的陷阱需要注意：
- **著色器兼容性**：確保使用的著色器版本支持轉換回饋功能。某些低版本的 WebGL 可能不支持此功能。
- **數據格式問題**：轉換回饋的緩衝區必須與著色器中的輸出類型匹配，否則可能會導致錯誤或不正確的數據。
- **繪製調用限制**：在 `beginTransformFeedback` 和 `endTransformFeedback` 之間，不能進行其他的繪製調用，否則會導致意外的行為。

## 一句總結
WebGLTransformFeedback 允許開發者在 WebGL 中高效地捕獲著色器輸出，從而提高圖形渲染性能。