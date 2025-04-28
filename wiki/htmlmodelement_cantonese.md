<!--
Meta Description: # HTMLModElement：JavaScript 中的 HTML 修改元素 ## 概述 `HTMLModElement` 是一種表示 HTML 中 `<ins>` 和 `<del>` 標籤的介面，這些標籤用於表示文本的插入和刪除。透過 JavaScript，開發者可以動態地操控這些元素，增強網...
Meta Keywords: htmlmodelement, html, ins, del, datetime
-->

# HTMLModElement：JavaScript 中的 HTML 修改元素

## 概述
`HTMLModElement` 是一種表示 HTML 中 `<ins>` 和 `<del>` 標籤的介面，這些標籤用於表示文本的插入和刪除。透過 JavaScript，開發者可以動態地操控這些元素，增強網頁的互動性和可讀性。

## 文檔
### 目的
`HTMLModElement` 主要用於表示文檔中的修改標記。這些標記通常用於顯示內容的變更，如編輯歷史或版本控制。

### 使用方法
在 JavaScript 中，`HTMLModElement` 提供了訪問和操作 `<ins>` 和 `<del>` 標籤的屬性。這包括以下屬性：
- `cite`：一個字符串，表示修改的來源或引用。
- `dateTime`：一個字符串，表示修改的日期和時間。

### 例子
以下是如何使用 `HTMLModElement` 的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>HTMLModElement 示例</title>
</head>
<body>
    <p>這是一些內容。<del>這是被刪除的部分。</del> <ins>這是新增的內容。</ins></p>

    <script>
        // 獲取 del 元素
        const delElement = document.querySelector('del');
        delElement.cite = 'https://example.com/old-version';
        delElement.dateTime = '2023-10-10T10:00:00Z';

        // 獲取 ins 元素
        const insElement = document.querySelector('ins');
        insElement.cite = 'https://example.com/new-version';
        insElement.dateTime = '2023-10-10T12:00:00Z';

        console.log(delElement);
        console.log(insElement);
    </script>
</body>
</html>
```

## 解釋
在使用 `HTMLModElement` 時，開發者需要注意以下幾點：
- 確保引用的 URL 是有效的，否則可能會導致無法正確顯示。
- 使用 `dateTime` 時，需遵循 ISO 8601 格式，以確保兼容性。
- 不要將 `cite` 和 `dateTime` 用於非 `<ins>` 或 `<del>` 標籤，因為這可能會引起錯誤或無法預期的行為。

## 總結
`HTMLModElement` 提供了一個有效的方法來操作和顯示 HTML 中的文本修改，讓開發者能夠動態地管理內容的變更。