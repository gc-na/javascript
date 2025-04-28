<!--
Meta Description: # JavaScript 的 onresize 事件：監控瀏覽器窗口大小變化 ## 簡介 `onresize` 是一個 JavaScript 事件，用於監控瀏覽器窗口大小的變化。當用戶調整窗口的大小時，這個事件會被觸發，允許開發者在窗口尺寸改變時執行特定的代碼。 ## 文檔 `onresize` 事...
Meta Keywords: onresize, window, javascript, box, function
-->

# JavaScript 的 onresize 事件：監控瀏覽器窗口大小變化

## 簡介
`onresize` 是一個 JavaScript 事件，用於監控瀏覽器窗口大小的變化。當用戶調整窗口的大小時，這個事件會被觸發，允許開發者在窗口尺寸改變時執行特定的代碼。

## 文檔
`onresize` 事件是 `window` 對象的一個屬性。當窗口的大小改變時，系統會自動調用與該事件關聯的函數。這對於需要根據顯示裝置的可用空間自適應布局或重新計算元素位置的應用特別有用。

### 使用方式
要使用 `onresize` 事件，您只需將一個函數指派給 `window.onresize`，如下所示：

```javascript
window.onresize = function() {
    // 當窗口大小改變時執行的代碼
    console.log('窗口大小已改變！');
};
```

### 事件屬性
- **target**: 事件發生的對象，通常是 `window`。
- **currentTarget**: 當前處理該事件的對象。

## 範例
以下是一些基本的 `onresize` 使用示例：

### 範例 1：簡單的窗口調整監控
```javascript
window.onresize = function() {
    console.log('當前窗口大小：' + window.innerWidth + 'x' + window.innerHeight);
};
```

### 範例 2：調整元素樣式
```javascript
const box = document.getElementById('box');

window.onresize = function() {
    if (window.innerWidth < 600) {
        box.style.backgroundColor = 'red';
    } else {
        box.style.backgroundColor = 'green';
    }
};
```

## 解釋
使用 `onresize` 時，開發者需要注意以下幾點：

1. **性能問題**：如果在 `onresize` 事件中執行重計算或重繪的操作，可能會導致性能下降，特別是在快速調整窗口大小的情況下。建議使用防抖（debounce）或節流（throttle）技術來減少函數調用的頻率。

2. **事件清除**：在某些情況下，您可能需要清除 `onresize` 事件的監聽器，以避免內存泄漏或舊的回調函數繼續執行。
   ```javascript
   window.onresize = null; // 清除事件
   ```

3. **兼容性**：`onresize` 事件在所有主流瀏覽器中都被支持，但在某些老舊的瀏覽器中可能會有差異，開發者應該進行兼容性測試。

## 一行總結
`onresize` 事件允許開發者在瀏覽器窗口大小變化時執行代碼，是創建響應式設計的重要工具。