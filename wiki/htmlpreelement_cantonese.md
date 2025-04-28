<!--
Meta Description: # HTMLPreElement：JavaScript 中的預格式化文本元素 ## 概述 `HTMLPreElement` 是一個代表 HTML `<pre>` 標籤的 JavaScript 介面，該標籤用於顯示預格式化的文本，通常用於顯示程式碼或其他需要保留空格和換行的內容。 ## 文件說明 `H...
Meta Keywords: htmlpreelement, html, pre, preelement, javascript
-->

# HTMLPreElement：JavaScript 中的預格式化文本元素

## 概述
`HTMLPreElement` 是一個代表 HTML `<pre>` 標籤的 JavaScript 介面，該標籤用於顯示預格式化的文本，通常用於顯示程式碼或其他需要保留空格和換行的內容。

## 文件說明
`HTMLPreElement` 繼承自 `HTMLElement`，用於操作和訪問 `<pre>` 標籤的屬性和方法。這個元素的主要目的是保持文本的格式，因為它會保留所有空格和換行符，這在顯示程式碼或其他格式化文本時特別重要。

### 用途
- 使文本以固定寬度的字型顯示，通常用於顯示程式碼。
- 保留文本中的空格和換行，確保文本的原始格式不會被打亂。

### 使用方法
在 JavaScript 中，可以使用 `document.createElement()` 方法來創建一個新的 `<pre>` 元素，並通過 DOM 操作將其添加到 HTML 文件中。

```javascript
// 創建一個新的 <pre> 元素
const preElement = document.createElement('pre');
preElement.textContent = '這是一個預格式化的文本示例。\n保留空格和換行。';
// 將其添加到 body 中
document.body.appendChild(preElement);
```

## 示例
以下是使用 `HTMLPreElement` 顯示程式碼的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>HTMLPreElement 示例</title>
</head>
<body>
    <script>
        const preElement = document.createElement('pre');
        preElement.textContent = `
function helloWorld() {
    console.log("Hello, World!");
}`;
        document.body.appendChild(preElement);
    </script>
</body>
</html>
```

## 解釋
在使用 `HTMLPreElement` 時，有一些常見的注意事項：

1. **空格和換行**：確保使用 `textContent` 而不是 `innerHTML` 來避免 HTML 解析問題。這樣可以正確顯示空格和換行。
2. **樣式**：可以通過 CSS 自定義 `<pre>` 標籤的樣式，例如字型、顏色等，但要注意這可能會影響文本的可讀性。
3. **可訪問性**：對於某些使用者，顯示大量格式化文本可能會影響可讀性，因此需考慮可訪問性設計。

## 一句總結
`HTMLPreElement` 是一個用於顯示預格式化文本的 JavaScript 接口，能夠保留空格和換行，適合用於展示程式碼或格式化內容。