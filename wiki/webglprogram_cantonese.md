<!--
Meta Description: # WebGLProgram：JavaScript 中的 WebGL 程序 ## 簡介 WebGLProgram 是 WebGL API 中的一個重要組件，用於管理和編譯圖形渲染的著色器程序。它使開發者能夠將頂點著色器和片段著色器結合到一起，從而渲染高效的 3D 圖形。 ## 文檔 ### 目的 W...
Meta Keywords: const, webglprogram, program, webgl, vertexshader
-->

# WebGLProgram：JavaScript 中的 WebGL 程序

## 簡介
WebGLProgram 是 WebGL API 中的一個重要組件，用於管理和編譯圖形渲染的著色器程序。它使開發者能夠將頂點著色器和片段著色器結合到一起，從而渲染高效的 3D 圖形。

## 文檔
### 目的
WebGLProgram 的主要目的是將頂點著色器和片段著色器結合成一個可執行的程序，這樣 GPU 就可以利用這個程序來進行圖形渲染。

### 使用方法
在使用 WebGLProgram 之前，開發者需要初始化 WebGL 上下文，然後創建著色器、編譯它們，最後將這些著色器鏈接到 WebGLProgram 中。以下是基本的使用步驟：

1. **創建 WebGL 上下文**：
   ```javascript
   const canvas = document.getElementById('canvas');
   const gl = canvas.getContext('webgl');
   ```

2. **創建和編譯著色器**：
   ```javascript
   const vertexShaderSource = `...`; // 頂點著色器代碼
   const fragmentShaderSource = `...`; // 片段著色器代碼

   const vertexShader = gl.createShader(gl.VERTEX_SHADER);
   gl.shaderSource(vertexShader, vertexShaderSource);
   gl.compileShader(vertexShader);

   const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
   gl.shaderSource(fragmentShader, fragmentShaderSource);
   gl.compileShader(fragmentShader);
   ```

3. **創建 WebGLProgram**：
   ```javascript
   const program = gl.createProgram();
   gl.attachShader(program, vertexShader);
   gl.attachShader(program, fragmentShader);
   gl.linkProgram(program);
   ```

4. **使用 WebGLProgram**：
   ```javascript
   gl.useProgram(program);
   ```

### 詳細信息
- **屬性**：WebGLProgram 實例不具備屬性，但可以通過 WebGL API 獲取有關著色器的詳細信息。
- **錯誤處理**：在編譯和鏈接過程中，應檢查任何錯誤，以確保著色器程序正確運行。

## 範例
以下是一個簡單的範例，展示如何創建和使用 WebGLProgram：

```javascript
// 創建 WebGL 上下文
const canvas = document.getElementById('canvas');
const gl = canvas.getContext('webgl');

// 頂點著色器和片段著色器的源代碼
const vertexShaderSource = `
  attribute vec4 a_position;
  void main(void) {
    gl_Position = a_position;
  }
`;

const fragmentShaderSource = `
  void main(void) {
    gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // 紅色
  }
`;

// 創建和編譯著色器
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);

// 創建 WebGLProgram
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// 使用 WebGLProgram
gl.useProgram(program);
```

## 解釋
在使用 WebGLProgram 時，開發者經常會遇到以下問題：

- **著色器編譯錯誤**：如果著色器代碼存在語法錯誤，則編譯將失敗。開發者應使用 `gl.getShaderInfoLog(shader)` 獲取錯誤信息。
- **鏈接失敗**：鏈接過程中可能出現未找到屬性或變數的錯誤。確保著色器中的所有變數都正確聲明並使用。

## 一句總結
WebGLProgram 是用於將頂點著色器和片段著色器結合在一起的 WebGL API 組件，對於 3D 渲染至關重要。