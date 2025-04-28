<!--
Meta Description: # WebGLShader: 用於 JavaScript 的 3D 圖形著色器 ## 簡介 WebGLShader 是一種用於 WebGL 的著色器對象，允許開發者在 JavaScript 中編寫自定義的圖形渲染程式碼。這使得開發者能夠創建高品質的 3D 圖形效果。 ## 文檔 ### 目的 Web...
Meta Keywords: const, webgl, webglshader, javascript, canvas
-->

# WebGLShader: 用於 JavaScript 的 3D 圖形著色器

## 簡介
WebGLShader 是一種用於 WebGL 的著色器對象，允許開發者在 JavaScript 中編寫自定義的圖形渲染程式碼。這使得開發者能夠創建高品質的 3D 圖形效果。

## 文檔
### 目的
WebGLShader 主要用於創建和編譯著色器程式，這些程式用於控制 WebGL 中的圖形渲染過程。著色器是小型的程序，通常用於計算圖形的顏色、光照和其他視覺效果。

### 使用方法
在 JavaScript 中使用 WebGLShader 的基本步驟如下：
1. 獲取 WebGL 上下文。
2. 創建一個著色器對象。
3. 編譯著色器源碼。
4. 處理編譯錯誤（如有）。
5. 將著色器附加到著色器程序。

以下是一個簡單的著色器創建流程：

```javascript
// 獲取 WebGL 上下文
const canvas = document.getElementById('canvas');
const gl = canvas.getContext('webgl');

// 創建頂點著色器
const vertexShaderSource = `
    attribute vec4 a_position;
    void main(void) {
        gl_Position = a_position;
    }
`;
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

// 檢查編譯錯誤
if (gl.getShaderParameter(vertexShader, gl.COMPILE_STATUS) === false) {
    console.error(gl.getShaderInfoLog(vertexShader));
}

// 創建片段著色器
const fragmentShaderSource = `
    void main(void) {
        gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0);
    }
`;
const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);

// 檢查編譯錯誤
if (gl.getShaderParameter(fragmentShader, gl.COMPILE_STATUS) === false) {
    console.error(gl.getShaderInfoLog(fragmentShader));
}

// 創建著色器程序並附加著色器
const shaderProgram = gl.createProgram();
gl.attachShader(shaderProgram, vertexShader);
gl.attachShader(shaderProgram, fragmentShader);
gl.linkProgram(shaderProgram);
```

## 示例
下面是一個簡單的示例，顯示如何使用 WebGLShader 創建一個紅色的三角形：

```javascript
const canvas = document.getElementById('canvas');
const gl = canvas.getContext('webgl');

// 顯示三角形的頂點數據
const vertices = new Float32Array([
    0,  1,
   -1, -1,
    1, -1,
]);

// 創建並綁定緩衝區
const vertexBuffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, vertexBuffer);
gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW);

// 創建著色器
const vertexShaderSource = `...`; // 參考上面的頂點著色器
const fragmentShaderSource = `...`; // 參考上面的片段著色器

// 編譯和連接著色器
const shaderProgram = gl.createProgram();
// 附加和鏈接著色器的代碼...

// 繪製
gl.clearColor(0.0, 0.0, 0.0, 1.0);
gl.clear(gl.COLOR_BUFFER_BIT);
gl.useProgram(shaderProgram);
gl.drawArrays(gl.TRIANGLES, 0, 3);
```

## 解釋
- **常見陷阱**: 編譯著色器時，未檢查編譯狀態可能會導致難以排查的錯誤。建議始終檢查 `gl.getShaderParameter(shader, gl.COMPILE_STATUS)` 的返回值。
- **性能考量**: 每次渲染時重複編譯著色器會影響性能，應該將其編譯為靜態資源並重複使用。
- **著色器語言**: WebGL 使用 GLSL ES，語言特性和標準可能與其他 GLSL 版本有所不同。

## 一句總結
WebGLShader 是在 JavaScript 中創建和編譯自定義著色器的關鍵對象，能夠實現豐富的 3D 圖形效果。