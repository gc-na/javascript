<!--
Meta Description: # FocusEvent 在 JavaScript 的應用 ## 概述 FocusEvent 是 JavaScript 中的一種事件，主要用於處理元素獲得或失去焦點的情況，尤其在表單元素和可互動元素中非常常見。 ## 文檔 FocusEvent 的主要用途是讓開發者能夠監控和響應用戶在頁面中的焦點變...
Meta Keywords: focus, focusevent, input, inputelement, blur
-->

# FocusEvent 在 JavaScript 的應用

## 概述
FocusEvent 是 JavaScript 中的一種事件，主要用於處理元素獲得或失去焦點的情況，尤其在表單元素和可互動元素中非常常見。

## 文檔
FocusEvent 的主要用途是讓開發者能夠監控和響應用戶在頁面中的焦點變化。這些事件包括 `focus` 和 `blur`，分別在元素獲得焦點和失去焦點時觸發。

### 使用方法
要使用 FocusEvent，您可以通過添加事件監聽器來捕獲焦點事件。例如：

```javascript
const inputElement = document.getElementById('myInput');

inputElement.addEventListener('focus', (event) => {
    console.log('Input has gained focus!');
});

inputElement.addEventListener('blur', (event) => {
    console.log('Input has lost focus!');
});
```

在這個範例中，當用戶點擊或選中輸入框時，`focus` 事件會被觸發；當用戶點擊其他地方使輸入框失去焦點時，`blur` 事件則會被觸發。

### 事件屬性
FocusEvent 物件提供了一些有用的屬性，如下：

- `relatedTarget`：返回與當前事件相關的元素，通常是在焦點移動時來自的元素。

## 範例
以下是 FocusEvent 的基本用法例子：

```html
<input type="text" id="myInput" placeholder="Click here...">

<script>
const inputElement = document.getElementById('myInput');

inputElement.addEventListener('focus', () => {
    console.log('Input is focused.');
});

inputElement.addEventListener('blur', () => {
    console.log('Input lost focus.');
});
</script>
```

在此範例中，當用戶點擊輸入框時，控制台會顯示 "Input is focused."，而當用戶點擊其他地方使輸入框失去焦點時，則會顯示 "Input lost focus."。

## 解釋
使用 FocusEvent 時，常見的陷阱包括：

- 確保對事件的監聽器正確添加，特別是在 DOM 元素進行動態加載時。
- 注意 `focus` 和 `blur` 事件不會冒泡，因此無法在父元素上捕獲這些事件。
- 在某些瀏覽器中，某些元素（如 `<input>` 和 `<textarea>`）的焦點行為可能會有所不同，需進行測試以確保一致性。

## 一句總結
FocusEvent 是用於捕捉和響應用戶與表單元素互動的關鍵事件。