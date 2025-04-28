<!--
Meta Description: # onwebkitAnimationEnd：JavaScript 動畫結束事件 ## 概述 `onwebkitAnimationEnd` 是一個 JavaScript 事件，用於偵測 CSS 動畫結束時的觸發。它是 `animationend` 事件的 WebKit 前綴版本，主要用於舊版的瀏覽器...
Meta Keywords: onwebkitanimationend, javascript, myelement, css, addeventlistener
-->

# onwebkitAnimationEnd：JavaScript 動畫結束事件

## 概述
`onwebkitAnimationEnd` 是一個 JavaScript 事件，用於偵測 CSS 動畫結束時的觸發。它是 `animationend` 事件的 WebKit 前綴版本，主要用於舊版的瀏覽器，如 Safari 和某些版本的 Chrome。

## 文檔
### 目的
`onwebkitAnimationEnd` 事件在 CSS 動畫完成後被觸發，通常用於執行後續操作，例如移除類別、執行其他 JavaScript 函數或改變元素的樣式。

### 使用方法
你可以將 `onwebkitAnimationEnd` 直接設置為一個 DOM 元素的屬性，或者使用 `addEventListener` 方法來監聽此事件。

#### 語法範例
```javascript
element.onwebkitAnimationEnd = function(event) {
    console.log("動畫結束");
};
```

或者使用 `addEventListener`：
```javascript
element.addEventListener('webkitAnimationEnd', function(event) {
    console.log("動畫結束");
});
```

### 詳細說明
- **事件物件**：當事件被觸發時，會傳遞一個事件物件，其中包含有關動畫的信息。
- **多個動畫**：如果同時有多個動畫，`onwebkitAnimationEnd` 會為每個動畫分別觸發。

## 範例
以下是一個簡單的範例，展示如何使用 `onwebkitAnimationEnd` 來偵測動畫的結束。

```html
<div id="myElement" class="animated"></div>

<style>
.animated {
    animation: fadeOut 2s forwards;
}

@keyframes fadeOut {
    from { opacity: 1; }
    to { opacity: 0; }
}
</style>

<script>
const myElement = document.getElementById('myElement');

myElement.onwebkitAnimationEnd = function() {
    console.log('動畫結束，元素已淡出');
};
</script>
```

## 解釋
### 常見問題
1. **不支援的瀏覽器**：在某些較新版本的瀏覽器中，建議使用不帶前綴的 `animationend` 事件。
2. **多個動畫**：如果元素上有多個動畫，必須注意確定是哪一個動畫結束，因為每個動畫都會觸發此事件。
3. **事件移除**：如果不再需要此事件，可以用 `removeEventListener` 方法移除監聽器。

## 總結
`onwebkitAnimationEnd` 是用來偵測 CSS 動畫結束的一個 JavaScript 事件，適合在舊版瀏覽器中使用。