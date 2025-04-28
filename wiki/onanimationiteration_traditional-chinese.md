<!--
Meta Description: # JavaScript 的 onanimationiteration 事件詳細介紹 ## 摘要 `onanimationiteration` 是一個用於動畫的事件，當 CSS 動畫每次重複時會觸發此事件。在 JavaScript 中，開發者可以透過此事件來執行特定的操作或更新 UI。 ## 文件說...
Meta Keywords: onanimationiteration, javascript, css, element, animatedelement
-->

# JavaScript 的 onanimationiteration 事件詳細介紹

## 摘要
`onanimationiteration` 是一個用於動畫的事件，當 CSS 動畫每次重複時會觸發此事件。在 JavaScript 中，開發者可以透過此事件來執行特定的操作或更新 UI。

## 文件說明
`onanimationiteration` 事件屬於 DOM 事件，專門用於監聽 CSS 動畫的迭代。當一個動畫完成一個循環並開始下一個循環時，此事件會被觸發。這對於需要在動畫過程中進行互動或更新狀態的應用特別有用。

### 目的
使用 `onanimationiteration` 可以讓開發者輕鬆管理動畫的行為，例如在每次動畫迭代時改變元素的樣式或執行其他 JavaScript 函數。

### 使用方法
`onanimationiteration` 可以直接在 DOM 元素上設置，也可以透過 JavaScript 代碼來添加事件監聽器。以下是基本的使用範例：

```javascript
const element = document.getElementById('animatedElement');

element.onanimationiteration = function() {
    console.log('動畫迭代一次');
};
```

### 詳細資訊
- **事件物件**: 事件處理函數接收一個事件物件作為參數，這個物件包含有關事件的詳細資訊，例如動畫名稱和目標元素。
- **多個動畫**: 如果一個元素同時有多個 CSS 動畫，`onanimationiteration` 事件會為每個動畫單獨觸發。
- **瀏覽器支持**: 大多數現代瀏覽器都支持此事件，但在舊版本的瀏覽器上可能存在兼容性問題。

## 範例
以下是一個基本的範例，展示如何使用 `onanimationiteration` 事件：

```html
<div id="animatedElement" class="my-animation"></div>

<style>
.my-animation {
    animation: bounce 2s infinite;
}

@keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
    }
    40% {
        transform: translateY(-30px);
    }
    60% {
        transform: translateY(-15px);
    }
}
</style>

<script>
const element = document.getElementById('animatedElement');

element.onanimationiteration = function(event) {
    console.log('動畫名稱: ' + event.animationName);
    // 在這裡可以添加自定義的邏輯
};
</script>
```

## 解釋
在使用 `onanimationiteration` 時，有幾個常見的陷阱和注意事項：

1. **性能考量**: 在每次動畫迭代時都觸發的操作可能影響性能，特別是在重複頻率較高的動畫中，應謹慎使用。
2. **事件移除**: 如果需要移除事件監聽器，應使用 `removeEventListener` 方法，而不是直接設置為 `null`。
3. **CSS 動畫必須定義**: 確保在使用此事件之前，CSS 動畫已正確定義，否則事件將不會被觸發。

## 一行總結
`onanimationiteration` 事件允許開發者在 CSS 動畫每次重複時執行 JavaScript 代碼，增強動畫的互動性和可控性。