<!--
Meta Description: # onanimationstart：JavaScript 中的動畫啟動事件 ## 概述 `onanimationstart` 是一個 JavaScript 事件，用於在 CSS 動畫開始時觸發特定的功能。這個事件通常與 DOM 元素的動畫屬性結合使用，能夠讓開發者在動畫正式開始時執行特定操作。 #...
Meta Keywords: onanimationstart, javascript, css, event, html
-->

# onanimationstart：JavaScript 中的動畫啟動事件

## 概述
`onanimationstart` 是一個 JavaScript 事件，用於在 CSS 動畫開始時觸發特定的功能。這個事件通常與 DOM 元素的動畫屬性結合使用，能夠讓開發者在動畫正式開始時執行特定操作。

## 文檔
### 目的
`onanimationstart` 事件的主要目的是讓開發者能夠監聽並響應 CSS 動畫的開始時刻。這對於需要在動畫開始時初始化狀態或執行某些邏輯的應用程序特別有用。

### 使用方法
`onanimationstart` 事件可以通過 JavaScript 直接在元素上設置，或者使用事件監聽器來處理。

#### 語法：
```javascript
element.onanimationstart = function(event) {
    // 事件處理邏輯
};
```
或者使用 `addEventListener` 方法：
```javascript
element.addEventListener('animationstart', function(event) {
    // 事件處理邏輯
});
```

### 詳細信息
- **事件對象**：當 `onanimationstart` 事件觸發時，會傳遞一個事件對象，其中包含有關動畫的信息，例如動畫名稱、持續時間等。
- **多個動畫**：如果一個元素同時有多個動畫，可以通過事件對象中的 `animationName` 屬性來識別是哪一個動畫觸發了事件。
- **瀏覽器支持**：大多數現代瀏覽器均支持 `onanimationstart` 事件，但建議檢查特定版本的兼容性。

## 範例
### 基本用法
下面是一個簡單的範例，展示如何使用 `onanimationstart` 事件。

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onanimationstart 示例</title>
    <style>
        .animate {
            animation: exampleAnimation 2s forwards;
        }

        @keyframes exampleAnimation {
            from { background-color: red; }
            to { background-color: yellow; }
        }
    </style>
</head>
<body>
    <div id="box" class="animate" style="width: 100px; height: 100px;"></div>
    <script>
        const box = document.getElementById('box');
        box.onanimationstart = function(event) {
            console.log('動畫開始，動畫名稱:', event.animationName);
        };
    </script>
</body>
</html>
```

## 解釋
### 常見陷阱
1. **事件未觸發**：確保元素上有正確的 CSS 動畫應用，否則 `onanimationstart` 將不會被觸發。
2. **多重動畫**：如果一個元素同時有多個動畫，可能會導致混淆，建議使用事件對象來確認是哪個動畫觸發的事件。
3. **性能考慮**：在大量元素上使用 `onanimationstart` 可能會影響性能，建議合理使用。

## 一句總結
`onanimationstart` 事件讓開發者能夠在 CSS 動畫開始時執行自定義邏輯，增強用戶體驗。