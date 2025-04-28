<!--
Meta Description: # WebGLShader：JavaScript 中的 WebGL 着色器 ## 概要 WebGLShader 是 WebGL API 中用於表示著色器的對象，著色器是 WebGL 程式中的一段程式碼，負責執行圖形渲染中的各種計算和操作。 ## 文件說明 WebGLShader 是用於創建和管理著色...
Meta Keywords: shader, webglshader, webgl, const, glsl
-->

# WebGLShader：JavaScript 中的 WebGL 着色器

## 概要
WebGLShader 是 WebGL API 中用於表示著色器的對象，著色器是 WebGL 程式中的一段程式碼，負責執行圖形渲染中的各種計算和操作。

## 文件說明
WebGLShader 是用於創建和管理著色器的主要構件。WebGL 支持兩種主要的著色器類型：頂點著色器和片元著色器。這些著色器使用 GLSL（OpenGL Shading Language）進行編寫，並在 GPU 上執行。開發者可以利用 WebGLShader 來實現圖形的高度自定義渲染效果。

### 目的
WebGLShader 的主要目的是提供一種方式來定義圖形的渲染過程，通過編寫著色器來執行特定的計算，這些計算可能包括顏色計算、光照計算、紋理映射等。

### 使用方式
要創建一個 WebGLShader，您需要經過以下步驟：
1. 獲取 WebGL 上下文。
2. 使用 `gl.createShader(type)` 方法創建著色器對象。
3. 使用 `gl.shaderSource(shader, source)` 方法將 GLSL 代碼源賦值給著色器。
4. 使用 `gl.compileShader(shader)` 方法編譯著色器。

### 參數
- `type`: 指定著色器的類型，可為 `gl.VERTEX_SHADER`（頂點著色器）或 `gl.FRAGMENT_SHADER`（片元著色器）。
- `source`: 一個字符串，包含 GLSL 代碼。

## 範例
以下是創建和編譯頂點著色器和片元著色器的基本範例：

```javascript
// 獲取 WebGL 上下文
const canvas = document.getElementById('canvas');
const gl = canvas.getContext('webgl');

// 頂點著色器 GLSL 代碼
const vertexShaderSource = `
    attribute vec4 a_position;
    void main(void) {
        gl_Position = a_position;
    }
`;

// 片元著色器 GLSL 代碼
const fragmentShaderSource = `
    void main(void) {
        gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // 紅色
    }
`;

// 創建和編譯著色器
function createShader(type, source) {
    const shader = gl.createShader(type);
    gl.shaderSource(shader, source);
    gl.compileShader(shader);
    // 檢查編譯狀態
    if (!gl.getShaderParameter(shader, gl.COMPILE_STATUS)) {
        console.error('Shader compilation failed: ' + gl.getShaderInfoLog(shader));
        gl.deleteShader(shader);
        return null;
    }
    return shader;
}

// 創建頂點和片元著色器
const vertexShader = createShader(gl.VERTEX_SHADER, vertexShaderSource);
const fragmentShader = createShader(gl.FRAGMENT_SHADER, fragmentShaderSource);
```

## 解釋
在使用 WebGLShader 時，開發者需要注意以下幾點：
- **編譯錯誤**：如果 GLSL 代碼有錯誤，該著色器將無法成功編譯。使用 `gl.getShaderInfoLog(shader)` 可以獲取錯誤信息。
- **著色器類型**：確保創建的著色器類型正確，頂點著色器和片元著色器有不同的用途和要求。
- **資源管理**：使用完著色器後，應使用 `gl.deleteShader(shader)` 釋放資源，避免內存泄漏。

## 單行摘要
WebGLShader 是 WebGL 中的著色器對象，用於定義圖形渲染的計算過程。