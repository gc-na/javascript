<!--
Meta Description: # HTMLTimeElement 於 JavaScript 中的應用 ## 概要 HTMLTimeElement 係一個代表 HTML `<time>` 標籤嘅 JavaScript 對象，呢個標籤用來表示時間或日期嘅信息，喺網頁中提供結構化時間數據，方便搜索引擎及應用程式讀取。 ## 文檔 HT...
Meta Keywords: time, htmltimeelement, html, datetime, timeelement
-->

# HTMLTimeElement 於 JavaScript 中的應用

## 概要
HTMLTimeElement 係一個代表 HTML `<time>` 標籤嘅 JavaScript 對象，呢個標籤用來表示時間或日期嘅信息，喺網頁中提供結構化時間數據，方便搜索引擎及應用程式讀取。

## 文檔
HTMLTimeElement 主要用於處理網頁中嘅 `<time>` 元素，佢可以用來讀取、修改或者設置時間或日期嘅相關屬性。佢具有以下特性：

- **屬性**：
  - `datetime`：用來指定時間或日期嘅標準化格式。
  - `innerText`：用來獲取或設置時間顯示嘅文字。

- **方法**：HTMLTimeElement 本身冇特定嘅方法，但可以使用 DOM 操作方法來修改或者訪問 `<time>` 標籤。

### 用法
要使用 HTMLTimeElement，首先需要在 HTML 文檔中創建一個 `<time>` 標籤，例如：

```html
<time datetime="2023-10-31T14:30">2023年10月31日 14:30</time>
```

然後，可以使用 JavaScript 來訪問呢個元素：

```javascript
const timeElement = document.querySelector('time');
console.log(timeElement.datetime); // 輸出：2023-10-31T14:30
```

## 示例
以下係一個基本使用的示例：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTMLTimeElement 示例</title>
</head>
<body>
    <time datetime="2023-10-31T14:30">2023年10月31日 14:30</time>

    <script>
        const timeElement = document.querySelector('time');
        console.log(timeElement.innerText); // 輸出：2023年10月31日 14:30
        console.log(timeElement.datetime);   // 輸出：2023-10-31T14:30
        timeElement.innerText = "萬聖節"; // 修改顯示時間
    </script>
</body>
</html>
```

## 解釋
使用 HTMLTimeElement 時，常見嘅陷阱包括：

- **格式不正確**：`datetime` 屬性必須遵循 ISO 8601 格式，否則可能無法正確解析。
- **DOM 操作**：確保在 DOM 完全加載後再訪問或操作 `<time>` 元素，以避免 `null` 錯誤。

另外，HTMLTimeElement 雖然本身冇太多方法，但可以使用標準的 DOM 操作來進行更複雜的交互。

## 一句總結
HTMLTimeElement 係一個用於操作 HTML `<time>` 標籤嘅 JavaScript 對象，方便網頁處理時間和日期數據。