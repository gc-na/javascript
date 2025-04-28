<!--
Meta Description: # requestAnimationFrame：提升 JavaScript 動畫性能的最佳實踐 ## 摘要 `requestAnimationFrame` 是一個用於在瀏覽器中創建高效動畫的 JavaScript 函式。它使開發者能夠在每次重繪之前執行動畫邏輯，從而優化性能和流暢度。 ## 文檔 #...
Meta Keywords: requestanimationframe, javascript, start, box, animate
-->

# requestAnimationFrame：提升 JavaScript 動畫性能的最佳實踐

## 摘要
`requestAnimationFrame` 是一個用於在瀏覽器中創建高效動畫的 JavaScript 函式。它使開發者能夠在每次重繪之前執行動畫邏輯，從而優化性能和流暢度。

## 文檔

### 目的
`requestAnimationFrame` 的主要目的是讓開發者能夠在瀏覽器的重繪周期中執行動畫，這樣可以確保動畫在每一幀中都能獲得最佳性能，並且節省資源，因為它自動調整執行頻率以適應顯示器的刷新率。

### 使用方法
`requestAnimationFrame` 是一個全局方法，可以這樣調用：

```javascript
requestAnimationFrame(callback);
```

- **callback**：一個函式，當瀏覽器準備好下一幀時會被調用。這個函式接受一個參數，該參數是當前時間戳（以毫秒為單位）。

### 詳細說明
- `requestAnimationFrame` 提供了一種在動畫中獲得平滑過渡的方式，並且能夠有效減少 CPU 和 GPU 的負擔。
- 當調用 `requestAnimationFrame` 時，瀏覽器會將此請求放入渲染隊列中，並在適當的時間執行。
- 如果使用 `setTimeout` 或 `setInterval` 來控制動畫，可能會導致性能問題和不一致的幀速率。

## 示例

### 簡單動畫示例
以下是一個使用 `requestAnimationFrame` 的簡單動畫示例：

```javascript
let start = null;
const box = document.getElementById('box');

function animate(timestamp) {
    if (!start) start = timestamp;
    const progress = timestamp - start;

    box.style.transform = 'translateX(' + Math.min(progress / 10, 200) + 'px)';

    if (progress < 2000) { // 動畫持續2秒
        requestAnimationFrame(animate);
    }
}

requestAnimationFrame(animate);
```

### 步驟說明
1. 定義一個起始時間 `start` 和目標元素 `box`。
2. `animate` 函式計算動畫的進度並更新元素位置。
3. 當進度小於2000毫秒時，繼續調用 `requestAnimationFrame`。

## 解釋

### 常見陷阱
- **無限循環**：如果不小心，可能會造成無限呼叫 `requestAnimationFrame`，導致性能下降。確保在適當的條件下停止動畫。
- **過度使用**：不必要的多次調用可能會影響性能，應該根據需求進行優化。
- **計算量大**：在回調函式中執行密集計算會導致動畫卡頓，應將計算移至其他位置，或減少每幀的計算量。

### 附加說明
- `requestAnimationFrame` 會自動在頁面隱藏或切換到其他標籤時停止調用，這樣可以節省資源。
- 在移動設備上，`requestAnimationFrame` 可以進一步優化，因為它對電池壽命的影響較小。

## 單行摘要
`requestAnimationFrame` 是一種高效的 JavaScript 方法，用於在瀏覽器中創建流暢的動畫，提升性能和資源利用率。