<!--
Meta Description: # WebGLActiveInfo：JavaScript中的WebGL活躍信息 ## 簡介 `WebGLActiveInfo` 是WebGL API中的一個重要接口，用於描述著色器中活躍變量的屬性。這些屬性包括變量的名稱、類型和大小，對於開發者在進行圖形渲染時非常重要。 ## 文檔 `WebGLAc...
Meta Keywords: var, webglactiveinfo, program, type, info
-->

# WebGLActiveInfo：JavaScript中的WebGL活躍信息

## 簡介
`WebGLActiveInfo` 是WebGL API中的一個重要接口，用於描述著色器中活躍變量的屬性。這些屬性包括變量的名稱、類型和大小，對於開發者在進行圖形渲染時非常重要。

## 文檔
`WebGLActiveInfo` 主要用於獲取著色器程序中活躍變量的詳細信息。當你使用 `getProgramInfoLog()` 或 `getActiveAttrib()`、`getActiveUniform()` 方法時，這個接口會返回相應的活躍變量信息。

### 用法
- **屬性**：
  - `size`：表示變量的數量（例如，對於向量變量，該值會顯示其維度）。
  - `type`：表示變量的數據類型，例如 `gl.FLOAT`、`gl.INT` 等。
  - `name`：變量的名稱，這是你在著色器代碼中定義的名稱。

### 創建示例
以下是如何使用 `WebGLActiveInfo` 的簡單示例：

```javascript
// 獲取WebGL上下文
var canvas = document.getElementById('canvas');
var gl = canvas.getContext('webgl');

// 編譯著色器
var vertexShader = gl.createShader(gl.VERTEX_SHADER);
// 省略著色器源代碼和編譯步驟

var fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
// 省略著色器源代碼和編譯步驟

var program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// 獲取活躍變量的數據
var numAttributes = gl.getProgram(program, gl.ACTIVE_ATTRIBUTES);
for (var i = 0; i < numAttributes; i++) {
    var info = gl.getActiveAttrib(program, i);
    console.log('Attribute Name: ' + info.name);
    console.log('Attribute Size: ' + info.size);
    console.log('Attribute Type: ' + info.type);
}
```

## 解釋
使用 `WebGLActiveInfo` 時，需要注意以下幾點：

1. **活躍變量的數量**：在查詢活躍屬性或統一變量之前，確保你已經成功編譯和鏈接著色器程序。
2. **變量類型的轉換**：`type` 屬性返回的是整數代碼，對於不同的變量類型，開發者需要參考WebGL文檔來獲取對應的類型名稱。
3. **命名**：著色器中變量的命名必須正確，否則 `WebGLActiveInfo` 將返回空的或錯誤的數據。

## 總結
`WebGLActiveInfo` 是一個用於描述WebGL著色器中活躍變量屬性的接口，對於開發者理解和使用WebGL至關重要。