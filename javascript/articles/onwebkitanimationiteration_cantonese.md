<!--
Meta Description: # JavaScript 中的 onwebkitanimationiteration 事件 ## 簡介 `onwebkitanimationiteration` 是一個用於處理 CSS 動畫迭代次數的事件，當動畫完成一個迭代時觸發。這個事件主要用於 WebKit 瀏覽器（如 Chrome 和 Saf...
Meta Keywords: onwebkitanimationiteration, javascript, box, css, event
-->

# JavaScript 中的 onwebkitanimationiteration 事件

## 簡介
`onwebkitanimationiteration` 是一個用於處理 CSS 動畫迭代次數的事件，當動畫完成一個迭代時觸發。這個事件主要用於 WebKit 瀏覽器（如 Chrome 和 Safari），以便在動畫循環時執行特定的 JavaScript 代碼。

## 文檔
### 目的
`onwebkitanimationiteration` 事件允許開發者在 CSS 動畫每次完成一個迭代時執行自定義的 JavaScript 代碼，這對於需要在動畫過程中進行狀態更新或界面變化的應用場景非常有用。

### 用法
要使用 `onwebkitanimationiteration` 事件，您需要將事件處理程序添加到 DOM 元素上。這可以通過直接設置事件屬性或使用 `addEventListener` 方法來實現。

### 詳細資訊
- **屬性**: `onwebkitanimationiteration` 是一個事件處理程序屬性，屬於 HTML 元素。
- **事件對象**: 當事件觸發時，會傳遞一個事件對象，該對象包含有關事件的詳細信息。
- **瀏覽器兼容性**: 此事件主要針對 WebKit 瀏覽器，對於其他瀏覽器（如 Firefox 或 Edge），建議使用標準的 `animationiteration` 事件。

## 範例
### 基本用法
```javascript
const box = document.querySelector('.animated-box');

box.onwebkitanimationiteration = function(event) {
    console.log('動畫迭代完成: ', event);
};
```

### 使用 addEventListener
```javascript
const box = document.querySelector('.animated-box');

box.addEventListener('webkitAnimationIteration', function(event) {
    console.log('動畫迭代完成: ', event);
});
```

## 解釋
### 常見問題
- **事件不觸發**: 如果動畫沒有正確設置或沒有觸發，請檢查 CSS 動畫的關鍵幀設置及其持續時間。
- **不兼容的瀏覽器**: 在非 WebKit 瀏覽器中，使用 `animationiteration` 事件，而非 `onwebkitanimationiteration`。

### 注意事項
- 確保動畫的 `animation-iteration-count` 屬性設置為大於 1 的值，否則事件將不會觸發。
- 當使用 `onwebkitanimationiteration` 時，確保 CSS 動畫的名稱與 JavaScript 中的選擇器相匹配。

## 總結
`onwebkitanimationiteration` 事件在 CSS 動畫的每次迭代時觸發，方便開發者在動畫中實現更豐富的互動。