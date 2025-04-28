<!--
Meta Description: # HTMLTextAreaElement：JavaScript 中的文本區域元素 ## 概述 `HTMLTextAreaElement` 係一個用於處理 HTML 文本區域元素嘅 JavaScript 物件，主要用於用戶輸入多行文本。透過此物件，開發者可以更方便地存取和操作文本區域嘅屬性和方法。 ...
Meta Keywords: htmltextareaelement, html, javascript, textarea, value
-->

# HTMLTextAreaElement：JavaScript 中的文本區域元素

## 概述
`HTMLTextAreaElement` 係一個用於處理 HTML 文本區域元素嘅 JavaScript 物件，主要用於用戶輸入多行文本。透過此物件，開發者可以更方便地存取和操作文本區域嘅屬性和方法。

## 文件
`HTMLTextAreaElement` 代表 HTML 中嘅 `<textarea>` 標籤，通常用於表單中收集用戶輸入嘅長文本資料。呢個物件提供咗多個屬性和方法，讓開發者可以控制文本區域嘅行為與外觀。

### 目的
`HTMLTextAreaElement` 嘅主要目的係為用戶提供一個可以輸入多行文本嘅界面，並且通過 JavaScript 來操作這些文本。

### 使用方法
要使用 `HTMLTextAreaElement`，首先需要在 HTML 中定義 `<textarea>` 標籤，然後在 JavaScript 中通過 DOM 操作來訪問該元素。

#### 基本屬性
- `value`：獲取或設置文本區域內顯示嘅文本。
- `rows`：獲取或設置文本區域顯示嘅行數。
- `cols`：獲取或設置文本區域顯示嘅列數。
- `placeholder`：獲取或設置文本區域的佔位符文本。

#### 基本方法
- `focus()`：將焦點設置到文本區域。
- `select()`：選擇文本區域內的文本。

## 示例
以下係一個簡單嘅示例，展示點樣使用 `HTMLTextAreaElement`：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>HTMLTextAreaElement 示例</title>
</head>
<body>
    <textarea id="myTextArea" rows="4" cols="50" placeholder="請輸入文本..."></textarea>
    <button onclick="submitText()">提交</button>

    <script>
        function submitText() {
            const textArea = document.getElementById('myTextArea');
            alert('您輸入嘅文本係：' + textArea.value);
        }
    </script>
</body>
</html>
```

## 解釋
- **常見問題**：開發者需要注意，當用戶輸入文本時，`value` 只會在表單提交時更新。如果要即時獲取文本，需使用事件監聽器。
- **注意事項**：文本區域默認不支持自動調整大小，如果需要此功能，可能需要額外的 CSS 或 JavaScript 來實現。

## 一句總結
`HTMLTextAreaElement` 係 JavaScript 中用於操作多行文本輸入元素嘅重要物件。