<!--
Meta Description: # onanimationend：JavaScript 動畫結束事件的完整指南 ## 概述 `onanimationend` 是一個 JavaScript 事件，用於監聽 CSS 動畫結束的時刻。當一個 CSS 動畫完成時，這個事件會被觸發，使開發者能夠執行相應的後續操作。 ## 文件說明 `ona...
Meta Keywords: onanimationend, javascript, box, css, animationend
-->

# onanimationend：JavaScript 動畫結束事件的完整指南

## 概述
`onanimationend` 是一個 JavaScript 事件，用於監聽 CSS 動畫結束的時刻。當一個 CSS 動畫完成時，這個事件會被觸發，使開發者能夠執行相應的後續操作。

## 文件說明
`onanimationend` 事件屬於 Animation Events，它的主要目的是提供一個回調機制，讓開發者能夠在動畫結束後執行特定的 JavaScript 代碼。這對於需要在特定動畫結束後進行 DOM 更新或觸發其他動作的情境非常有用。

### 用法
要使用 `onanimationend` 事件，您需要將其綁定到一個 DOM 元素上。當動畫結束時，會觸發指定的回調函數。以下是基本的使用方法：

```javascript
const element = document.querySelector('.animated-element');

element.addEventListener('animationend', function() {
    console.log('動畫已結束！');
});
```

在上述代碼中，我們選擇了一個具有 `.animated-element` 類的元素，並為其添加了一個 `animationend` 事件監聽器。

## 範例
以下是幾個簡單的示例，演示如何使用 `onanimationend` 事件。

### 示例 1：基本用法
```javascript
const box = document.getElementById('box');

box.addEventListener('animationend', () => {
    alert('動畫已經完成！');
});
```

### 示例 2：多重動畫
如果一個元素有多個動畫，您可以使用 `event` 參數來識別是哪一個動畫結束。

```javascript
const box = document.getElementById('box');

box.addEventListener('animationend', (event) => {
    if (event.animationName === 'fadeIn') {
        console.log('fadeIn 動畫結束');
    } else if (event.animationName === 'fadeOut') {
        console.log('fadeOut 動畫結束');
    }
});
```

## 解釋
使用 `onanimationend` 時，開發者應注意以下幾點：

1. **多次觸發**：如果一個元素在同一時間內有多個動畫，`animationend` 事件會為每個動畫觸發一次。
2. **CSS 動畫的支持**：確保所用的 CSS 動畫已正確定義，否則該事件將無法觸發。
3. **性能考量**：在動畫結束時執行大量 JavaScript 代碼可能會導致性能問題，建議適度使用。

## 一句總結
`onanimationend` 事件允許開發者在 CSS 動畫結束時執行特定操作，提升了用戶互動體驗。