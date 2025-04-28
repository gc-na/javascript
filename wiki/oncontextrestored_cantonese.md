<!--
Meta Description: # oncontextrestored：JavaScript 中的上下文恢復事件 ## 概述 `oncontextrestored` 是一個與 HTML5 Canvas 相關的事件，通常用於處理畫布的上下文恢復，讓開發者在上下文被恢復時執行特定的操作。 ## 文檔 ### 目的 `oncontext...
Meta Keywords: canvas, oncontextrestored, ctx, const, 100
-->

# oncontextrestored：JavaScript 中的上下文恢復事件

## 概述
`oncontextrestored` 是一個與 HTML5 Canvas 相關的事件，通常用於處理畫布的上下文恢復，讓開發者在上下文被恢復時執行特定的操作。

## 文檔
### 目的
`oncontextrestored` 事件在 Canvas 的繪圖上下文（如 2D 或 WebGL）被恢復後觸發。這對於需要在用戶操作後重繪畫布的情境非常重要，例如在圖形編輯器中，當用戶撤銷或重做操作時。

### 使用方法
要使用 `oncontextrestored` 事件，開發者需要將其作為事件監聽器附加到 Canvas 元素的上下文上。這樣可以在上下文恢復後自動觸發指定的回調函數。

#### 語法範例
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// 設置上下文恢復事件
ctx.oncontextrestored = function(event) {
    console.log('上下文已恢復');
    // 在此處執行恢復後的邏輯
};
```

## 範例
以下是使用 `oncontextrestored` 的基本範例：

```html
<canvas id="myCanvas" width="500" height="500"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');

    // 畫一個矩形
    ctx.fillStyle = 'blue';
    ctx.fillRect(10, 10, 100, 100);

    // 設置上下文恢復事件
    ctx.oncontextrestored = function(event) {
        console.log('上下文已恢復');
        ctx.fillStyle = 'red';
        ctx.fillRect(20, 20, 100, 100);
    };

    // 模擬上下文恢復
    setTimeout(() => {
        ctx.restore();
    }, 2000);
</script>
```

## 解釋
使用 `oncontextrestored` 時，開發者需要注意以下幾點：

1. **事件觸發條件**：此事件僅在上下文被明確地恢復時觸發。確保正確使用 `save()` 和 `restore()` 方法來管理上下文狀態。
2. **性能考量**：過多的上下文恢復操作可能會影響性能，尤其是在高頻率繪圖的應用中。
3. **跨瀏覽器兼容性**：雖然大多數現代瀏覽器支持此事件，但在一些舊版本的瀏覽器中可能會存在兼容性問題，建議進行測試。

## 一句總結
`oncontextrestored` 事件允許開發者在 Canvas 上下文恢復後執行自定義操作，對於動態繪圖非常有用。