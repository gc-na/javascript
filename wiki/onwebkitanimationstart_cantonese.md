<!--
Meta Description: # onwebkitanimationstart：JavaScript 動畫事件的詳細介紹 ## 概述 `onwebkitanimationstart` 是一個與 WebKit 瀏覽器引擎相關的 JavaScript 事件，當 CSS 動畫開始時觸發。這個事件對於想要在動畫開始時執行特定操作的開發者...
Meta Keywords: onwebkitanimationstart, css, html, javascript, webkit
-->

# onwebkitanimationstart：JavaScript 動畫事件的詳細介紹

## 概述
`onwebkitanimationstart` 是一個與 WebKit 瀏覽器引擎相關的 JavaScript 事件，當 CSS 動畫開始時觸發。這個事件對於想要在動畫開始時執行特定操作的開發者來說非常有用。

## 文檔
### 目的
`onwebkitanimationstart` 事件使開發者能夠在 CSS 動畫開始時執行 JavaScript 代碼。這對於處理動畫效果以及同步其他功能非常重要。

### 使用方法
要使用 `onwebkitanimationstart` 事件，您需要將其附加到一個 HTML 元素。在這個事件被觸發時，您可以指定一個回調函數來執行您想要的操作。

### 詳細信息
- **事件類型**：`AnimationEvent`
- **可用屬性**：
  - `animationName`：觸發事件的動畫名稱。
  - `elapsedTime`：自動畫開始以來經過的時間（以秒為單位）。
  - `pseudoElement`：如果是伪元素，則返回伪元素的名稱。

## 範例
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        @keyframes example {
            from { background-color: red; }
            to { background-color: yellow; }
        }

        .animate {
            animation-name: example;
            animation-duration: 4s;
        }
    </style>
    <title>onwebkitanimationstart 範例</title>
</head>
<body>
    <div class="animate" id="myElement" style="width:100px;height:100px;"></div>
    <script>
        const element = document.getElementById('myElement');
        element.onwebkitanimationstart = function(event) {
            console.log('動畫開始了: ' + event.animationName);
        };
    </script>
</body>
</html>
```

## 解釋
- **常見問題**：`onwebkitanimationstart` 事件主要在 WebKit 瀏覽器上有效，如 Safari。其他瀏覽器中可能需要使用標準的 `animationstart` 事件。
- **注意事項**：確保您的 CSS 動畫正確設置，否則事件可能無法觸發。另外，這個事件不會在 CSS 動畫重啟的時候再次觸發，僅在動畫初次開始時有效。

## 總結
`onwebkitanimationstart` 是一個專為 WebKit 瀏覽器設計的事件，讓開發者能夠在 CSS 動畫開始時執行 JavaScript 代碼。