<!--
Meta Description: # HTMLBaseElement：JavaScript 中的基礎元素 ## 概述 `HTMLBaseElement` 是一種表示 HTML 文檔中 `<base>` 標籤的接口。它允許開發者在 JavaScript 中操作與基礎 URL 相關的屬性，這對於相對路徑的資源加載非常重要。 ## 文檔 ...
Meta Keywords: url, base, href, html, htmlbaseelement
-->

# HTMLBaseElement：JavaScript 中的基礎元素

## 概述
`HTMLBaseElement` 是一種表示 HTML 文檔中 `<base>` 標籤的接口。它允許開發者在 JavaScript 中操作與基礎 URL 相關的屬性，這對於相對路徑的資源加載非常重要。

## 文檔
`HTMLBaseElement` 是一個 DOM 接口，提供了對應於 HTML `<base>` 標籤的屬性和方法。這個元素主要用於設定當前文檔的基礎 URL，這會影響到文檔中所有相對 URL 的解析。

### 目的
`<base>` 標籤的主要作用是為文檔中的所有相對 URL 提供一個基準路徑，這樣開發者可以更方便地管理資源的載入。

### 使用
要使用 `HTMLBaseElement`，開發者需要在 HTML 文檔中包含 `<base>` 標籤，然後可以通過 JavaScript 獲取和設置其屬性。

```html
<base href="https://www.example.com/">
```

在 JavaScript 中，可以這樣訪問和修改：

```javascript
const baseElement = document.querySelector('base');
console.log(baseElement.href); // 取得基礎 URL
baseElement.href = 'https://www.newexample.com/'; // 修改基礎 URL
```

### 屬性
- `href`: 獲取或設置基礎 URL 的屬性。這是一個字串，代表文檔的基礎路徑。

## 範例
以下是使用 `HTMLBaseElement` 的基本範例：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>HTMLBaseElement 範例</title>
    <base href="https://www.example.com/">
</head>
<body>
    <script>
        // 獲取 base 元素
        const baseElement = document.querySelector('base');
        
        // 輸出當前的 href
        console.log('當前基礎 URL:', baseElement.href);
        
        // 修改基礎 URL
        baseElement.href = 'https://www.newexample.com/';
        console.log('修改後的基礎 URL:', baseElement.href);
    </script>
</body>
</html>
```

在這個範例中，我們創建了一個 HTML 文檔，並使用 JavaScript 來獲取和修改 `<base>` 標籤的 `href` 屬性。

## 解釋
使用 `HTMLBaseElement` 時，有一些常見的注意事項：
1. **相對 URL 的影響**: 設置基礎 URL 後，文檔中的所有相對 URL 都會基於此 URL 進行解析。這可能會導致資源無法正確加載。
2. **多個 `<base>` 標籤**: 文檔中只能有一個 `<base>` 標籤。若存在多個，瀏覽器將根據標準行為僅使用第一個標籤的 `href`。
3. **動態修改**: 如果在文檔加載後動態修改 `<base>` 標籤的 `href`，這不會影響已經加載的資源，但會影響後續的相對路徑解析。

## 簡單總結
`HTMLBaseElement` 使得開發者能夠在 JavaScript 中輕鬆地操作 HTML 文檔的基礎 URL，從而影響相對路徑的資源加載。