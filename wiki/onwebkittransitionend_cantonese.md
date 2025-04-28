<!--
Meta Description: # onwebkittransitionend：JavaScript 中的過渡結束事件 ## Synopsis `onwebkittransitionend` 是一個 JavaScript 事件，當 CSS 轉場動畫結束時觸發，主要用於處理與過渡效果相關的回調功能。 ## Documentation...
Meta Keywords: onwebkittransitionend, box, javascript, webkit, html
-->

# onwebkittransitionend：JavaScript 中的過渡結束事件

## Synopsis
`onwebkittransitionend` 是一個 JavaScript 事件，當 CSS 轉場動畫結束時觸發，主要用於處理與過渡效果相關的回調功能。

## Documentation
`onwebkittransitionend` 是在 WebKit 瀏覽器引擎中使用的一個事件屬性，當一個 CSS 過渡結束後，會觸發此事件。這個事件適用於支持 WebKit 的瀏覽器，如 Safari 和某些版本的 Chrome。開發者可以通過這個事件來執行特定的 JavaScript 代碼，以響應過渡效果的完成。

### 目的
此事件的主要目的在於讓開發者能夠在過渡效果完成後執行相應的操作，如更新 UI 或觸發其他動畫。

### 使用方法
你可以將 `onwebkittransitionend` 屬性賦值為一個事件處理函數。當過渡結束時，這個函數將自動被調用。

```javascript
element.onwebkittransitionend = function(event) {
    // 處理過渡結束的邏輯
};
```

## Examples
### 基本用法範例
以下是使用 `onwebkittransitionend` 的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>onwebkittransitionend 示例</title>
    <style>
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            transition: background-color 2s;
        }
        .box.active {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div class="box" id="myBox"></div>
    <button id="toggle">切換顏色</button>

    <script>
        const box = document.getElementById('myBox');
        const button = document.getElementById('toggle');

        box.onwebkittransitionend = function() {
            alert('過渡已結束！');
        };

        button.onclick = function() {
            box.classList.toggle('active');
        };
    </script>
</body>
</html>
```

在這個範例中，當點擊按鈕切換顏色時，過渡結束後將彈出提示框。

## Explanation
### 常見陷阱及注意事項
1. **瀏覽器兼容性**：`onwebkittransitionend` 只在 WebKit 瀏覽器中有效。對於其他瀏覽器（如 Firefox 和 IE），需要使用標準事件 `transitionend`。
2. **多重過渡**：如果元素同時有多個過渡屬性，該事件可能會被觸發多次。開發者需要檢查 `event.propertyName` 來確保正確的過渡屬性被處理。
3. **事件清理**：在不再需要監聽事件時，應考慮移除事件處理器，以避免內存洩漏。

## One Line Summary
`onwebkittransitionend` 是一個 JavaScript 事件，用於響應 CSS 過渡效果結束，特別針對 WebKit 瀏覽器。