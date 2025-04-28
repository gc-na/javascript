<!--
Meta Description: # WebGLProgram：JavaScript中的WebGL程序 ## 概述 WebGLProgram是WebGL API中的一个重要对象，用于表示一个WebGL程序。它将顶点着色器和片段着色器组合在一起，以便在WebGL上下文中执行图形渲染。 ## 文档 ### 目的 WebGLProgram...
Meta Keywords: const, program, vertexshader, fragmentshader, javascript
-->

# WebGLProgram：JavaScript中的WebGL程序

## 概述
WebGLProgram是WebGL API中的一个重要对象，用于表示一个WebGL程序。它将顶点着色器和片段着色器组合在一起，以便在WebGL上下文中执行图形渲染。

## 文档
### 目的
WebGLProgram用于创建一个可在GPU上运行的着色器程序。该程序由顶点着色器和片段着色器组成，负责处理图形的几何形状和像素着色。

### 使用
在使用WebGLProgram之前，您需要先创建WebGL上下文，并编译着色器。以下是创建WebGLProgram的基本步骤：

1. **获取WebGL上下文**：
   ```javascript
   const canvas = document.getElementById('canvas');
   const gl = canvas.getContext('webgl');
   ```

2. **编写顶点着色器和片段着色器**：
   ```javascript
   const vertexShaderSource = `...`; // 顶点着色器源代码
   const fragmentShaderSource = `...`; // 片段着色器源代码
   ```

3. **创建着色器**：
   ```javascript
   const vertexShader = gl.createShader(gl.VERTEX_SHADER);
   gl.shaderSource(vertexShader, vertexShaderSource);
   gl.compileShader(vertexShader);
   
   const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
   gl.shaderSource(fragmentShader, fragmentShaderSource);
   gl.compileShader(fragmentShader);
   ```

4. **创建WebGLProgram**：
   ```javascript
   const program = gl.createProgram();
   gl.attachShader(program, vertexShader);
   gl.attachShader(program, fragmentShader);
   gl.linkProgram(program);
   ```

5. **使用程序**：
   ```javascript
   gl.useProgram(program);
   ```

### 细节
- WebGLProgram只在链接后被认为是有效的。确保在使用WebGLProgram之前调用`linkProgram`。
- 如果链接失败，可以使用`getProgramInfoLog`获取错误信息。
- WebGLProgram无法直接创建，必须通过`createProgram`方法生成。

## 示例
以下是使用WebGLProgram的基本示例：

```javascript
const canvas = document.getElementById('canvas');
const gl = canvas.getContext('webgl');

// 顶点着色器
const vertexShaderSource = `
attribute vec4 a_Position;
void main() {
    gl_Position = a_Position;
}
`;

// 片段着色器
const fragmentShaderSource = `
void main() {
    gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // 红色
}
`;

const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);

const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);
gl.useProgram(program);
```

## 说明
- **常见问题**：在链接程序时，如果着色器编译失败，WebGLProgram将无法链接。务必检查每个着色器的编译状态。
- **调试**：可以使用`gl.getProgramInfoLog(program)`查看链接过程中出现的任何错误信息。
- **性能考虑**：尽量减少对WebGLProgram的频繁切换，以提高渲染性能。

## 一句话总结
WebGLProgram是一个用于在WebGL中运行的着色器程序，它连接顶点和片段着色器以实现高效的图形渲染。