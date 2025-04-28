<!--
Meta Description: # WebGLProgram：JavaScript中的WebGL程序對象 ## 摘要 WebGLProgram是WebGL API中的一個重要對象，負責儲存和管理著色器程序的編譯結果，是在WebGL中進行3D圖形渲染的核心組件之一。 ## 文檔 ### 目的 WebGLProgram對象的主要目的是...
Meta Keywords: program, const, attachshader, useprogram, vertexshader
-->

# WebGLProgram：JavaScript中的WebGL程序對象

## 摘要
WebGLProgram是WebGL API中的一個重要對象，負責儲存和管理著色器程序的編譯結果，是在WebGL中進行3D圖形渲染的核心組件之一。

## 文檔
### 目的
WebGLProgram對象的主要目的是將頂點著色器和片段著色器的編譯結果組織在一起，形成一個完整的著色器程序。開發者需要先創建著色器，再將其附加到WebGLProgram，並最終使用該程序進行繪製操作。

### 使用方法
創建WebGLProgram的基本步驟如下：
1. 使用`gl.createProgram()`創建一個新的WebGLProgram對象。
2. 使用`gl.attachShader(program, shader)`將著色器附加到該程序。
3. 使用`gl.linkProgram(program)`來鏈接程序。
4. 使用`gl.useProgram(program)`來啟用該程序。

### 詳細信息
- **創建程序**：`gl.createProgram()`方法返回一個新的WebGLProgram對象。
- **附加著色器**：使用`gl.attachShader()`將頂點著色器和片段著色器附加到程序中。
- **鏈接程序**：調用`gl.linkProgram()`來編譯和鏈接所有附加的著色器。
- **使用程序**：調用`gl.useProgram()`來告訴WebGL當前要使用哪個程序來進行渲染。

## 示例
以下是一個基本的使用示例：

```javascript
// 獲取WebGL上下文
const canvas = document.getElementById('myCanvas');
const gl = canvas.getContext('webgl');

// 創建著色器
const vertexShaderSource = `...`; // 頂點著色器代碼
const fragmentShaderSource = `...`; // 片段著色器代碼

const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);

// 創建WebGLProgram
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// 使用程序
gl.useProgram(program);
```

## 解釋
在使用WebGLProgram時，開發者需要注意以下幾個常見問題：
- **著色器編譯錯誤**：在編譯著色器時，若源代碼存在語法錯誤，將導致編譯失敗，開發者應使用`gl.getShaderInfoLog(shader)`來檢查錯誤信息。
- **鏈接錯誤**：如果附加到程序的著色器不符合要求，鏈接過程將失敗，開發者可以使用`gl.getProgramInfoLog(program)`來獲取詳細錯誤信息。
- **使用程序**：確保在繪製之前正確調用`gl.useProgram(program)`，否則將不會使用該程序進行渲染。

## 單行摘要
WebGLProgram是WebGL API中負責管理著色器程序的關鍵對象，對於3D圖形渲染至關重要。