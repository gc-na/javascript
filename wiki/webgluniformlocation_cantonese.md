<!--
Meta Description: # WebGLUniformLocation：JavaScript中的WebGL Uniform位置 ## 概述 WebGLUniformLocation 是 WebGL 中用於表示著色器中 uniform 變數位置的對象。透過這個對象，開發者可以向 GPU 發送 uniform 數據，以便在渲染過...
Meta Keywords: uniform, const, webgluniformlocation, getuniformlocation, program
-->

# WebGLUniformLocation：JavaScript中的WebGL Uniform位置

## 概述
WebGLUniformLocation 是 WebGL 中用於表示著色器中 uniform 變數位置的對象。透過這個對象，開發者可以向 GPU 發送 uniform 數據，以便在渲染過程中使用。

## 文檔
### 目的
WebGLUniformLocation 的主要目的是提供一種方法，使開發者能夠獲取並引用 WebGL 著色器中的 uniform 變數。這使得在渲染時可以方便地傳遞不同的數據（如顏色、矩陣等）給著色器。

### 使用方式
在使用 WebGLUniformLocation 前，開發者需要先獲取該變數的位置信息。這通常通過 `gl.getUniformLocation` 方法來實現。以下是基本的使用流程：

1. 編寫著色器代碼，定義 uniform 變數。
2. 編譯並鏈接著色器。
3. 使用 `gl.getUniformLocation` 獲取該 uniform 的位置。
4. 使用 `gl.uniform*` 系列函數來設置該 uniform 的值。

### 詳細信息
- **創建和獲取位置**：在使用 `gl.getUniformLocation` 時，需要提供著色器程序和 uniform 變數的名稱。
- **uniform 變數類型**：根據不同的數據類型（如浮點數、整數、向量、矩陣等），使用不同的 `gl.uniform*` 方法來設置值。
- **性能考量**：頻繁地更改 uniform 變數可能會影響性能，因此應該合理安排更新頻率。

## 示例
以下是使用 WebGLUniformLocation 的基本範例：

```javascript
// 初始化 WebGL 上下文
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl');

// 編寫著色器代碼
const vertexShaderSource = `
attribute vec4 position;
void main() {
    gl_Position = position;
}
`;

const fragmentShaderSource = `
precision mediump float;
uniform vec4 u_color;
void main() {
    gl_FragColor = u_color;
}
`;

// 編譯著色器
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);

// 創建著色器程序
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// 獲取 uniform 位置
const uColorLocation = gl.getUniformLocation(program, 'u_color');

// 使用 uniform
gl.useProgram(program);
gl.uniform4f(uColorLocation, 1.0, 0.0, 0.0, 1.0); // 設置顏色為紅色
```

## 解釋
使用 WebGLUniformLocation 時，開發者需要注意以下幾點：
- **變數名稱必須正確**：確保在 `getUniformLocation` 中使用的名稱與著色器代碼中的名稱完全一致，區分大小寫。
- **著色器必須已鏈接**：在獲取 uniform 位置之前，確保著色器已成功編譯和鏈接。
- **性能優化**：避免在每一幀中重複調用 `getUniformLocation`，應在初始化階段獲取並保存位置。

## 總結
WebGLUniformLocation 是 WebGL 中的關鍵組件，允許開發者在著色器中操作 uniform 變數，從而影響渲染過程。