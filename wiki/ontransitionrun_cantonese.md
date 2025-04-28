<!--
Meta Description: # ontransitionrun：JavaScript 的過渡效果事件 ## 概述 `ontransitionrun` 是一個用於監聽 CSS 過渡效果開始的 JavaScript 事件。當 CSS 過渡開始時，此事件會被觸發，允許開發者執行特定的操作或效果。 ## 文件說明 ### 目的 `on...
Meta Keywords: ontransitionrun, css, javascript, box, 過渡開始時
-->

# ontransitionrun：JavaScript 的過渡效果事件

## 概述
`ontransitionrun` 是一個用於監聽 CSS 過渡效果開始的 JavaScript 事件。當 CSS 過渡開始時，此事件會被觸發，允許開發者執行特定的操作或效果。

## 文件說明
### 目的
`ontransitionrun` 事件的主要目的是讓開發者能夠在 CSS 過渡開始時獲得通知。這對於在過渡效果啟動時執行 JavaScript 操作非常有用，例如改變其他元素的狀態或觸發動畫。

### 使用方法
要使用 `ontransitionrun` 事件，您可以將事件處理器附加到 DOM 元素上。當指定的 CSS 過渡開始時，事件處理器會被調用。

### 事件屬性
- **target**: 觸發事件的元素。
- **propertyName**: 觸發過渡的 CSS 屬性名稱。
- **elapsedTime**: 到目前為止經過的過渡時間。

### 例子
以下是如何使用 `ontransitionrun` 事件的基本示例：

```javascript
// 獲取目標元素
const box = document.querySelector('.box');

// 設置過渡效果
box.style.transition = 'all 2s';

// 設置 ontransitionrun 事件處理器
box.ontransitionrun = function(event) {
    console.log('過渡開始:', event.propertyName);
};

// 觸發過渡效果的函數
function startTransition() {
    box.style.transform = 'translateX(100px)';
}

// 點擊按鈕時開始過渡
document.querySelector('.start-button').addEventListener('click', startTransition);
```

## 解釋
使用 `ontransitionrun` 時，開發者需注意以下幾點：
- 如果過渡效果未正確設置或CSS屬性不支持過渡，事件將不會被觸發。
- `ontransitionrun` 事件會對每個過渡效果觸發一次，若元素同時有多個過渡效果，則會多次觸發。
- 確保在設置過渡效果之前已經定義了 CSS 樣式，否則可能無法預期地運行。

## 總結
`ontransitionrun` 是一個用來監聽 CSS 過渡開始的事件，能幫助開發者在過渡效果啟動時執行特定的 JavaScript 操作。