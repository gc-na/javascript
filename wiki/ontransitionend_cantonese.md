<!--
Meta Description: # ontransitionend：JavaScript 的過渡結束事件 ## 概述 `ontransitionend` 是一個 JavaScript 事件，當 CSS 過渡效果完成時會被觸發。這個事件對於需要在過渡結束時執行特定操作的開發者來說非常有用。 ## 文檔 `ontransitionen...
Meta Keywords: ontransitionend, css, addeventlistener, event, box
-->

# ontransitionend：JavaScript 的過渡結束事件

## 概述
`ontransitionend` 是一個 JavaScript 事件，當 CSS 過渡效果完成時會被觸發。這個事件對於需要在過渡結束時執行特定操作的開發者來說非常有用。

## 文檔
`ontransitionend` 事件屬於 HTML DOM 事件，主要用於監聽元素的 CSS 過渡結束。當一個元素的 CSS 屬性完成過渡時，會觸發這個事件，開發者可以在事件處理函數中執行進一步的操作。

### 用法
可以通過將事件處理器直接指定給一個 DOM 元素的 `ontransitionend` 屬性，或使用 `addEventListener` 方法來監聽這個事件。

#### 示例代碼：
```javascript
const element = document.getElementById('myElement');

// 使用 ontransitionend
element.ontransitionend = function(event) {
    console.log('過渡已完成！', event.propertyName);
};

// 使用 addEventListener
element.addEventListener('transitionend', function(event) {
    console.log('過渡已完成！', event.propertyName);
});
```

## 示例
### 基本用法
以下是一個簡單的示例，當方塊過渡結束時，改變其顏色：

```html
<div id="box" style="width:100px; height:100px; background-color:red; transition: background-color 1s;"></div>
<button id="start">開始過渡</button>

<script>
    const box = document.getElementById('box');
    const button = document.getElementById('start');

    button.addEventListener('click', function() {
        box.style.backgroundColor = 'blue';
    });

    box.addEventListener('transitionend', function() {
        console.log('顏色過渡已完成！');
    });
</script>
```

## 解釋
### 常見問題
1. **事件不觸發**：確保 CSS 過渡屬性已正確設置。若過渡效果未正確應用，則 `ontransitionend` 將不會被觸發。
2. **多個過渡**：如果同一元素有多個過渡屬性，則每個過渡結束時都會觸發 `ontransitionend`。可以通過 `event.propertyName` 來判斷是哪個屬性觸發的事件。

### 注意事項
- `ontransitionend` 事件會在過渡完成後立即觸發，但不會在過渡期間觸發。
- 請注意，某些瀏覽器可能對 `transitionend` 事件的支持有限，特別是在舊版瀏覽器中，開發者應考慮使用適當的前綴。

## 一句總結
`ontransitionend` 是用來監聽 CSS 過渡結束的 JavaScript 事件，能夠幫助開發者在過渡完成後執行特定操作。