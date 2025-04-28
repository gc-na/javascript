<!--
Meta Description: # onwebkitanimationend 事件在 JavaScript 中的應用 ## 概述 `onwebkitanimationend` 是一個與動畫結束事件有關的 JavaScript 事件，專門用於 WebKit 瀏覽器（如 Safari 和 Chrome）。當 CSS 動畫結束時，這個事...
Meta Keywords: onwebkitanimationend, element, javascript, css, myanimation
-->

# onwebkitanimationend 事件在 JavaScript 中的應用

## 概述
`onwebkitanimationend` 是一個與動畫結束事件有關的 JavaScript 事件，專門用於 WebKit 瀏覽器（如 Safari 和 Chrome）。當 CSS 動畫結束時，這個事件將被觸發，允許開發者執行特定的操作或邏輯。

## 文檔
### 目的
`onwebkitanimationend` 事件的主要目的是讓開發者能夠在 CSS 動畫結束時執行 JavaScript 代碼。這對於需要在動畫完成後進行更新或清理的應用程式特別有用，例如在動畫結束後顯示隱藏的元素或改變樣式。

### 使用方法
使用 `onwebkitanimationend` 事件需要將其作為事件處理器附加到 DOM 元素上。當指定的 CSS 動畫結束時，事件將被觸發，並執行相應的回調函數。

```javascript
const element = document.querySelector('.my-element');

element.style.animation = 'myAnimation 2s';

element.onwebkitanimationend = function() {
    console.log('Animation has ended');
    // 這裡可以添加更多的操作
};
```

### 詳細說明
- **事件屬性**：`onwebkitanimationend` 是一個屬性，可以直接賦值為一個函數，這個函數將在動畫結束時被調用。
- **事件物件**：事件處理器中可以訪問事件物件，該物件提供了動畫的詳細資訊，如動畫的名稱和持續時間。
- **兼容性**：`onwebkitanimationend` 是專為 WebKit 瀏覽器設計的，因此在其他瀏覽器（如 Firefox 和 Edge）中，應使用標準的 `animationend` 事件。

## 範例
### 基本用法
以下是一個基本範例，展示如何使用 `onwebkitanimationend` 事件：

```html
<div class="my-element">這是一個動畫元素</div>

<style>
.my-element {
    animation: myAnimation 2s;
}

@keyframes myAnimation {
    from { opacity: 0; }
    to { opacity: 1; }
}
</style>

<script>
const element = document.querySelector('.my-element');

element.onwebkitanimationend = function() {
    alert('動畫已結束！');
};
</script>
```

### 多個動畫
如果一個元素有多個動畫，則可以通過檢查 `event.animationName` 來確定具體是哪個動畫結束：

```javascript
element.onwebkitanimationend = function(event) {
    if (event.animationName === 'myAnimation') {
        console.log('特定動畫已結束');
    }
};
```

## 解釋
### 常見陷阱
- **不支援的瀏覽器**：請確保對不支持 `onwebkitanimationend` 的瀏覽器使用其他事件進行降級處理，例如 `animationend`。
- **事件名稱的區分**：確保正確使用 `onwebkitanimationend`，而不是 `onanimationend`。兩者是針對不同瀏覽器的實現。

### 注意事項
- 確保 CSS 動畫已正確定義，否則事件將不會被觸發。
- 使用 `addEventListener` 方法可以添加多個事件處理器，而不會覆蓋已存在的處理器。

## 一句話總結
`onwebkitanimationend` 事件允許開發者在 WebKit 瀏覽器中處理 CSS 動畫結束時的行為，是增強用戶體驗的有力工具。