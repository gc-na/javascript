<!--
Meta Description: # cancelAnimationFrame：JavaScript 中的動畫取消功能 ## 概要 `cancelAnimationFrame` 是一個 JavaScript 方法，用來取消先前使用 `requestAnimationFrame` 註冊的動畫幀請求。這個方法對於控制動畫的播放非常重要，...
Meta Keywords: cancelanimationframe, requestanimationframe, javascript, animationid, animate
-->

# cancelAnimationFrame：JavaScript 中的動畫取消功能

## 概要
`cancelAnimationFrame` 是一個 JavaScript 方法，用來取消先前使用 `requestAnimationFrame` 註冊的動畫幀請求。這個方法對於控制動畫的播放非常重要，可以防止不必要的重繪，從而提升性能。

## 文檔
### 目的
`cancelAnimationFrame` 的主要目的是停止一個由 `requestAnimationFrame` 註冊的動畫幀請求。這有助於在不需要更新畫面的情況下，減少計算資源的浪費，特別是在動畫不再需要進行時，例如用戶切換了頁面或關閉了視窗。

### 使用方法
```javascript
cancelAnimationFrame(id);
```

#### 參數
- `id`：一個整數，這是先前調用 `requestAnimationFrame` 返回的幀請求 ID。

### 詳情
- `cancelAnimationFrame` 只會取消由相應的 `requestAnimationFrame` 返回的請求。如果 `id` 無效或不存在，則不會產生任何效果。
- 當動畫不再需要時，例如用戶暫停或停止觀看動畫，應及時調用 `cancelAnimationFrame` 以釋放資源。
- 此方法並不會影響已經渲染的幀，只會取消未來的請求。

## 範例
### 基本用法
```javascript
let animationId;

function animate() {
    // 更新動畫邏輯...
    animationId = requestAnimationFrame(animate);
}

// 開始動畫
animate();

// 停止動畫
cancelAnimationFrame(animationId);
```

### 不再需要時取消
```javascript
let animationId;

function animate() {
    // 更新動畫邏輯...
    animationId = requestAnimationFrame(animate);
}

// 開始動畫
animate();

// 在某個條件下停止動畫，例如用戶按下按鈕
document.getElementById('stopButton').addEventListener('click', () => {
    cancelAnimationFrame(animationId);
});
```

## 解釋
使用 `cancelAnimationFrame` 時，有幾個常見的陷阱需要注意：
- 確保 `id` 是來自於有效的 `requestAnimationFrame` 調用；如果使用無效的 ID，則不會產生任何影響。
- 在動畫過程中，請妥善管理動畫 ID，以避免多次取消同一幀請求。
- 如果在動畫循環內不斷調用 `requestAnimationFrame`，需要在適當時機調用 `cancelAnimationFrame`，以避免持續的資源浪費。

## 一句總結
`cancelAnimationFrame` 是用來取消先前註冊的動畫幀請求的 JavaScript 方法，能夠有效控制動畫的運行和節省計算資源。