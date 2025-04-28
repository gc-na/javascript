<!--
Meta Description: # onanimationstart：JavaScript 動畫事件的深入解析 ## 概述 `onanimationstart` 是一個 JavaScript 事件，用於監聽 CSS 動畫的開始事件。當一個動畫開始播放時，這個事件會被觸發，開發者可以利用此事件來執行特定的 JavaScript 代碼...
Meta Keywords: onanimationstart, event, javascript, element, css
-->

# onanimationstart：JavaScript 動畫事件的深入解析

## 概述
`onanimationstart` 是一個 JavaScript 事件，用於監聽 CSS 動畫的開始事件。當一個動畫開始播放時，這個事件會被觸發，開發者可以利用此事件來執行特定的 JavaScript 代碼，以增強用戶互動體驗。

## 文檔
### 目的
`onanimationstart` 事件的主要目的是幫助開發者在 CSS 動畫開始時執行某些動作，例如更新用戶介面或記錄動畫狀態。

### 使用方法
`onanimationstart` 可以被用於任何 DOM 元素上。事件處理器可以通過直接在元素上設置，或者使用 JavaScript 的事件監聽器添加。此事件的基本語法如下：

```javascript
element.onanimationstart = function(event) {
  // 在動畫開始時執行的代碼
};
```

或者使用 `addEventListener` 方法：

```javascript
element.addEventListener('animationstart', function(event) {
  // 在動畫開始時執行的代碼
});
```

### 事件屬性
事件對象 `event` 包含多個屬性，最常用的有：
- `animationName`: 動畫的名稱。
- `elapsedTime`: 動畫從開始到事件觸發的時間（以秒為單位）。
- `target`: 觸發事件的元素。

## 示例
### 基本用法
以下是一個簡單的範例，在動畫開始時顯示一條消息：

```html
<div id="animatedElement" class="animate"></div>

<script>
  var element = document.getElementById('animatedElement');

  element.onanimationstart = function(event) {
    console.log('動畫 "' + event.animationName + '" 開始了！');
  };
</script>
```

### 使用 `addEventListener`
另一個範例，使用 `addEventListener` 來監聽動畫開始事件：

```html
<div id="animatedElement" class="animate"></div>

<script>
  var element = document.getElementById('animatedElement');

  element.addEventListener('animationstart', function(event) {
    alert('動畫 "' + event.animationName + '" 已開始！');
  });
</script>
```

## 解釋
- **常見陷阱**：`onanimationstart` 事件只會在動畫開始時觸發一次。如果動畫重複播放，則每次重啟動畫時都會觸發事件。
- **跨瀏覽器支持**：確保在使用 `onanimationstart` 前檢查瀏覽器的兼容性，特別是在舊版瀏覽器中。
- **CSS 動畫要求**：必須在 CSS 中明確定義動畫，否則事件無法正確觸發。

## 總結
`onanimationstart` 是一個強大的事件，可以幫助開發者在 CSS 動畫開始時執行自定義代碼，從而提升用戶體驗。