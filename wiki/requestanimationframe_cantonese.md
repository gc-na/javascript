<!--
Meta Description: # 使用 requestAnimationFrame 進行高效能動畫的 JavaScript 技術 ## 摘要 `requestAnimationFrame` 是一個用於創建平滑動畫的 JavaScript 方法，能夠在瀏覽器每次重繪時執行指定的函數，從而提高性能和節省資源。 ## 文檔 `requ...
Meta Keywords: requestanimationframe, javascript, pos, let, callback
-->

# 使用 requestAnimationFrame 進行高效能動畫的 JavaScript 技術

## 摘要
`requestAnimationFrame` 是一個用於創建平滑動畫的 JavaScript 方法，能夠在瀏覽器每次重繪時執行指定的函數，從而提高性能和節省資源。

## 文檔
`requestAnimationFrame` 的主要目的是幫助開發者以更高效的方式進行動畫和更新畫面。它可以自動調整動畫的幀率，與瀏覽器的重繪周期同步，從而提供更流暢的使用者體驗。

### 用法
`requestAnimationFrame` 的基本語法如下：

```javascript
let requestID = requestAnimationFrame(callback);
```

其中，`callback` 是在每次重繪時要執行的函數。當不再需要動畫時，可以使用 `cancelAnimationFrame(requestID)` 來停止動畫。

### 參數
- **callback**: 一個函數，當瀏覽器準備好重繪時將調用該函數，該函數會接收一個時間戳作為參數。

### 返回值
`requestAnimationFrame` 返回一個整數 ID，這個 ID 可以用於取消該動畫調用。

## 範例
以下是使用 `requestAnimationFrame` 的基本範例：

```javascript
let square = document.getElementById('square');
let pos = 0;

function animate() {
    pos += 1; // 每次更新位置
    square.style.transform = `translateX(${pos}px)`;
    
    if (pos < 500) { // 當位置小於 500px 時繼續動畫
        requestAnimationFrame(animate);
    }
}

requestAnimationFrame(animate);
```

在這個範例中，一個方形將從左向右移動，直到其位置達到 500 像素。

## 解釋
使用 `requestAnimationFrame` 時，有一些常見的注意事項和陷阱：

- **性能優化**: 與使用 `setTimeout` 或 `setInterval` 相比，`requestAnimationFrame` 更加高效，因為它能夠減少不必要的重繪，並根據瀏覽器的重繪頻率進行調整。
- **暫停動畫**: 當用戶切換到其他標籤頁或最小化瀏覽器時，`requestAnimationFrame` 會自動暫停，這有助於節省資源。
- **回調的時間戳**: `requestAnimationFrame` 提供的時間戳可以用來計算動畫的持續時間，這有助於創建平滑的過渡效果。

## 總結
`requestAnimationFrame` 是一個高效的 JavaScript 方法，專為創建流暢的動畫而設計，能夠有效地提升使用者體驗。