<!--
Meta Description: # WebGLContextEvent：JavaScript 的 WebGL 上下文事件 ## 概述 WebGLContextEvent 是一個用於處理 WebGL 上下文變更的事件，通常在 WebGL 應用中用於檢測和響應上下文的創建和銷毀。這個事件對於開發高效能的 3D 圖形應用程式至關重要。 ...
Meta Keywords: webgl, canvas, webglcontextevent, const, addeventlistener
-->

# WebGLContextEvent：JavaScript 的 WebGL 上下文事件

## 概述
WebGLContextEvent 是一個用於處理 WebGL 上下文變更的事件，通常在 WebGL 應用中用於檢測和響應上下文的創建和銷毀。這個事件對於開發高效能的 3D 圖形應用程式至關重要。

## 文檔
### 目的
WebGLContextEvent 提供了一個標準的事件接口，使開發者能夠在 WebGL 上下文狀態改變時（如上下文丟失或恢復）進行相應的處理。這對於確保應用穩定性和用戶體驗非常重要。

### 使用
WebGLContextEvent 是一個內建的事件，會在特定情況下自動觸發。開發者可以監聽此事件來處理上下文變更。

#### 事件類型
- `webglcontextlost`：當 WebGL 上下文丟失時觸發。
- `webglcontextrestored`：當 WebGL 上下文恢復時觸發。

### 事件屬性
- `statusMessage`：一個字符串，包含有關事件的附加信息。

### 監聽事件
要使用 WebGLContextEvent，開發者需要將事件監聽器附加到 WebGL 渲染上下文上：

```javascript
const canvas = document.getElementById("myCanvas");
const gl = canvas.getContext("webgl");

// 監聽上下文丟失事件
canvas.addEventListener("webglcontextlost", function(event) {
    event.preventDefault(); // 防止瀏覽器默認行為
    console.log("WebGL 上下文已丟失");
}, false);

// 監聽上下文恢復事件
canvas.addEventListener("webglcontextrestored", function() {
    console.log("WebGL 上下文已恢復");
}, false);
```

## 示例
以下是一個使用 WebGLContextEvent 的基本示例：

```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
const canvas = document.getElementById("myCanvas");
const gl = canvas.getContext("webgl");

canvas.addEventListener("webglcontextlost", function(event) {
    event.preventDefault();
    alert("WebGL 上下文丟失，請重新加載頁面。");
}, false);

canvas.addEventListener("webglcontextrestored", function() {
    alert("WebGL 上下文已恢復，開始渲染。");
    // 此處可以重新初始化 WebGL
}, false);
</script>
```

## 解釋
使用 WebGLContextEvent 時，開發者需要注意以下幾點：

- **上下文丟失**：當瀏覽器需要釋放資源時，WebGL 上下文可能會丟失，這時應用需要妥善處理，並提示用戶重新加載頁面。
- **性能考量**：在上下文恢復後，可能需要重新初始化資源（如著色器、紋理等），這可能會影響性能。
- **事件順序**：確保事件的處理順序正確，因為可能會在上下文丟失和恢復之間進行多次渲染。

## 單句總結
WebGLContextEvent 是一個重要的事件接口，用於處理 WebGL 上下文的丟失與恢復，對於保證 3D 應用的穩定性至關重要。