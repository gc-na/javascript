<!--
Meta Description: # TransitionEvent: JavaScript中的過渡事件 ## 簡介 TransitionEvent 是一個用於處理 CSS 過渡效果的 JavaScript 事件。當一個元素的過渡效果開始、結束或中斷時，會觸發此事件，讓開發者能夠對過渡狀態進行更精細的控制。 ## 文件說明 Tran...
Meta Keywords: transitionevent, box, css, event, button
-->

# TransitionEvent: JavaScript中的過渡事件

## 簡介
TransitionEvent 是一個用於處理 CSS 過渡效果的 JavaScript 事件。當一個元素的過渡效果開始、結束或中斷時，會觸發此事件，讓開發者能夠對過渡狀態進行更精細的控制。

## 文件說明
TransitionEvent 是一個繼承自 Event 的接口，專門用於描述 CSS 過渡過程中的事件。這些事件能夠讓開發者監控過渡的開始、結束及其持續時間等信息。當元素的 CSS transition 屬性改變時，會產生 TransitionEvent 事件。

### 主要用途
- 監聽 CSS 過渡的開始和結束
- 獲取過渡的相關信息，如持續時間、延遲等
- 增強用戶體驗，根據過渡狀態調整界面行為

### 使用方式
要使用 TransitionEvent，開發者需要為目標元素添加事件監聽器，並指定要監聽的事件類型。常見的事件類型包括：
- `transitionend`: 當過渡效果完成後觸發。

```javascript
const element = document.querySelector('.my-element');

element.addEventListener('transitionend', (event) => {
    console.log('過渡結束:', event.propertyName);
});
```

## 例子
以下是基本的使用範例，展示如何監聽過渡事件：

### HTML部分
```html
<div class="box" style="width: 100px; height: 100px; background-color: blue;"></div>
<button id="toggle">切換顏色</button>
```

### CSS部分
```css
.box {
    transition: background-color 1s ease;
}

.box.active {
    background-color: red;
}
```

### JavaScript部分
```javascript
const box = document.querySelector('.box');
const button = document.getElementById('toggle');

button.addEventListener('click', () => {
    box.classList.toggle('active');
});

box.addEventListener('transitionend', (event) => {
    console.log('過渡屬性:', event.propertyName);
});
```

在這個例子中，當按鈕被點擊時，`box` 的顏色會在藍色和紅色之間切換，並在過渡結束時打印出過渡屬性名稱。

## 解釋
在使用 TransitionEvent 時，開發者應注意以下幾點：
- 確保已正確設置 CSS transition 屬性，否則過渡事件將不會觸發。
- TransitionEvent 只在過渡完成後觸發，對於過渡過程中的其他狀態（如開始）則需要其他事件（如 `transitionstart`）。
- 在某些瀏覽器中，過渡事件的支持可能有所不同，建議進行相應的兼容性測試。

## 總結
TransitionEvent 是一個強大的工具，可幫助開發者有效地管理和監控 CSS 過渡效果的狀態，增強用戶體驗。