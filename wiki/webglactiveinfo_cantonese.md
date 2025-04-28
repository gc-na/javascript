<!--
Meta Description: # WebGLActiveInfo：JavaScript中的關鍵資料結構 ## 簡介 WebGLActiveInfo 是一個與 WebGL 相關的 JavaScript 物件，用來描述著色器中變數的資訊，例如變數的類型與名稱。這對於開發者在使用 WebGL 進行圖形渲染時，相當重要。 ## 文件資訊...
Meta Keywords: const, webglactiveinfo, webgl, shaderprogram, vertexshader
-->

# WebGLActiveInfo：JavaScript中的關鍵資料結構

## 簡介
WebGLActiveInfo 是一個與 WebGL 相關的 JavaScript 物件，用來描述著色器中變數的資訊，例如變數的類型與名稱。這對於開發者在使用 WebGL 進行圖形渲染時，相當重要。

## 文件資訊
### 目的
WebGLActiveInfo 主要用於提供有關著色器中活躍變數的詳細資訊。透過這個物件，開發者可以獲得變數的名字、類型以及大小，這些資訊對於正確使用著色器變數至關重要。

### 用法
要取得 WebGLActiveInfo 物件，開發者需要使用 `getActiveAttrib` 或 `getActiveUniform` 方法。這些方法會返回對應的 WebGLActiveInfo 物件。

### 詳情
- **屬性**：
  - `size`: 表示這個變數的數量（例如，對於向量類型，可能會是 2、3 或 4）。
  - `type`: 表示變數的資料類型，這通常是 WebGL 提供的常數，例如 `gl.FLOAT`、`gl.INT` 等。
  - `name`: 變數的名稱，這是開發者在著色器代碼中所定義的名稱。

## 範例
以下是如何使用 WebGLActiveInfo 的基本範例：

```javascript
// 獲取 WebGL 上下文
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl');

// 定義著色器
const vertexShaderSource = `...`; // 頂點著色器程式碼
const fragmentShaderSource = `...`; // 片段著色器程式碼

// 編譯著色器
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);

// 創建著色器程序
const shaderProgram = gl.createProgram();
gl.attachShader(shaderProgram, vertexShader);
gl.attachShader(shaderProgram, fragmentShader);
gl.linkProgram(shaderProgram);

// 獲取活躍變數資訊
const numAttributes = gl.getProgramParameter(shaderProgram, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttributes; i++) {
    const activeInfo = gl.getActiveAttrib(shaderProgram, i);
    console.log(`名稱: ${activeInfo.name}, 類型: ${activeInfo.type}, 大小: ${activeInfo.size}`);
}
```

## 解釋
在使用 WebGLActiveInfo 時，開發者需注意以下幾點：
- 確保著色器已成功編譯和鏈接，否則 `getActiveAttrib` 或 `getActiveUniform` 可能返回 `null`。
- 不同的 WebGL 實現可能對於變數的支持有所不同，因此在多種設備上測試是必要的。
- 如果變數在著色器中未被使用，則可能不會出現在活躍變數列表中。

## 簡單總結
WebGLActiveInfo 是一個提供有關 WebGL 著色器中活躍變數資訊的物件，對於圖形渲染至關重要。