<!--
Meta Description: # ontransitionstart：JavaScript 轉場事件的完整指南 ## 概要 `ontransitionstart` 是一個 JavaScript 事件，用於監聽 CSS 轉場效果開始的時刻。這個事件可以幫助開發者在元素開始進行轉場時觸發特定的 JavaScript 行為。 ## 文...
Meta Keywords: ontransitionstart, css, javascript, myelement, element
-->

# ontransitionstart：JavaScript 轉場事件的完整指南

## 概要
`ontransitionstart` 是一個 JavaScript 事件，用於監聽 CSS 轉場效果開始的時刻。這個事件可以幫助開發者在元素開始進行轉場時觸發特定的 JavaScript 行為。

## 文檔
### 目的
`ontransitionstart` 事件的主要目的是提供一種方式來響應 CSS 轉場的開始時間點，讓開發者可以執行一些動作，如改變樣式或觸發其他函數。

### 使用方法
要使用 `ontransitionstart` 事件，可以將它添加到一個 DOM 元素上。當 CSS 轉場開始時，這個事件會被觸發。以下是基本的用法：

```javascript
const element = document.getElementById('myElement');

element.addEventListener('transitionstart', (event) => {
    console.log('轉場開始:', event);
});
```

在這個例子中，當 `myElement` 開始進行 CSS 轉場時，控制台會輸出一條信息。

### 詳細說明
- **支持的瀏覽器**：`ontransitionstart` 在大多數主流瀏覽器中均得到支持，包括 Chrome、Firefox、Safari 及 Edge。
- **事件屬性**：在事件對象中，您可以獲取許多有用的屬性，如 `propertyName`（觸發轉場的 CSS 屬性），`elapsedTime`（轉場已經持續的時間）等。
- **CSS 轉場的設置**：要使用 `ontransitionstart`，必須確保元素的 CSS 已經設置了轉場屬性，例如：

```css
#myElement {
    transition: all 0.5s ease;
}
```

## 範例
以下是一個簡單的範例，展示如何使用 `ontransitionstart` 事件。

### HTML 代碼
```html
<div id="myElement" style="width: 100px; height: 100px; background-color: red;"></div>
<button id="startTransition">開始轉場</button>
```

### JavaScript 代碼
```javascript
const element = document.getElementById('myElement');
const button = document.getElementById('startTransition');

element.addEventListener('transitionstart', (event) => {
    console.log('轉場開始:', event.propertyName);
});

button.addEventListener('click', () => {
    element.style.width = '200px'; // 觸發轉場
});
```

在這個範例中，當用戶點擊按鈕時，`myElement` 的寬度將從 100px 增加到 200px，並且會觸發 `transitionstart` 事件。

## 解釋
- **常見問題**：如果您發現 `ontransitionstart` 事件沒有被觸發，請確保轉場屬性已正確設置，並且 CSS 動畫的開始狀態與結束狀態之間的變化是明顯的。
- **轉場時間**：`ontransitionstart` 事件只會在轉場開始的瞬間觸發，如果轉場的持續時間設置得太短，可能會錯過事件的捕捉。
- **多個轉場**：如果一個元素同時有多個轉場，`ontransitionstart` 事件會為每個轉場分別觸發。

## 一句總結
`ontransitionstart` 事件允許開發者在 CSS 轉場開始時觸發 JavaScript 行為，是增強網頁互動性的有力工具。