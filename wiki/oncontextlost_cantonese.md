<!--
Meta Description: # oncontextlost 事件在 JavaScript 中的應用 ## 概述 `oncontextlost` 是一個事件，主要用於 HTML5 的 Canvas API，當 WebGL 上下文丟失時觸發。這個事件對於處理圖形渲染和資源管理至關重要。 ## 文檔 `oncontextlost` ...
Meta Keywords: canvas, webgl, oncontextlost, event, const
-->

# oncontextlost 事件在 JavaScript 中的應用

## 概述
`oncontextlost` 是一個事件，主要用於 HTML5 的 Canvas API，當 WebGL 上下文丟失時觸發。這個事件對於處理圖形渲染和資源管理至關重要。

## 文檔
`oncontextlost` 事件的主要目的是讓開發者在 WebGL 上下文丟失時執行必要的清理和重新初始化操作。上下文丟失通常發生在瀏覽器的資源管理策略下，例如當瀏覽器需要釋放顯示卡的內存或當用戶切換到其他標籤頁時。

### 使用方法
要監聽 `oncontextlost` 事件，開發者需要將事件處理器附加到 Canvas 元素的上下文上：

```javascript
const canvas = document.getElementById('myCanvas');
const gl = canvas.getContext('webgl');

canvas.addEventListener('webglcontextlost', function(event) {
    event.preventDefault(); // 防止默認行為
    console.log('WebGL 上下文已丟失');
}, false);
```

在這段代碼中，當 WebGL 上下文丟失時，事件處理器將被觸發，並且可以在此處執行清理工作，如釋放資源。

## 示例
以下是 `oncontextlost` 的一個簡單示例，展示了如何處理上下文丟失：

```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const gl = canvas.getContext('webgl');

    canvas.addEventListener('webglcontextlost', function(event) {
        event.preventDefault(); // 防止默認的行為
        console.log('WebGL 上下文已丟失');
        // 這裡可以執行清理代碼
    }, false);
    
    canvas.addEventListener('webglcontextrestored', function() {
        console.log('WebGL 上下文已恢復');
        // 這裡可以重新初始化資源
    }, false);
</script>
```

## 解釋
在使用 `oncontextlost` 時，有一些常見的陷阱和注意事項：

1. **資源管理**：當上下文丟失時，所有的 WebGL 資源（如著色器、緩衝區等）將不再有效，因此需要在上下文恢復後重新創建這些資源。
   
2. **事件預防**：在事件處理器中調用 `event.preventDefault()` 是非常重要的，這可以防止瀏覽器執行默認的上下文丟失行為。

3. **性能考量**：過度監控上下文丟失事件可能會影響性能，應謹慎使用。

## 單行摘要
`oncontextlost` 事件在 WebGL 上下文丟失時觸發，幫助開發者處理資源釋放和重新初始化。