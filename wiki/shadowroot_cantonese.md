<!--
Meta Description: # ShadowRoot: 深入了解 JavaScript 中的影子根結構 ## 簡介 ShadowRoot 是一種 JavaScript 介面，用於創建 Web 組件的封閉 DOM 樹，讓開發者能夠將樣式和標記封裝在一個獨立的命名空間中，避免與主文檔的樣式和行為衝突。 ## 文檔 ### 目的 S...
Meta Keywords: shadowroot, div, dom, html, javascript
-->

# ShadowRoot: 深入了解 JavaScript 中的影子根結構

## 簡介
ShadowRoot 是一種 JavaScript 介面，用於創建 Web 組件的封閉 DOM 樹，讓開發者能夠將樣式和標記封裝在一個獨立的命名空間中，避免與主文檔的樣式和行為衝突。

## 文檔
### 目的
ShadowRoot 主要用於支持 Web 組件標準，提供一種方法來封裝組件的內部結構（例如，樣式和 DOM），並允許用戶在不干擾外部文檔的情況下進行組件的開發。

### 用法
要創建 ShadowRoot，開發者需要使用 `attachShadow` 方法，這個方法在一個 HTML 元素上被調用，並返回一個 ShadowRoot 實例。一般格式如下：

```javascript
let shadowRoot = element.attachShadow({ mode: 'open' | 'closed' });
```

- **mode**: 指定 ShadowRoot 的模式。`open` 模式允許外部腳本訪問 ShadowRoot，而 `closed` 模式則不允許。

### 詳細說明
- **開放與封閉模式**: 在 `open` 模式下，開發者可以通過 `element.shadowRoot` 訪問 ShadowRoot，而在 `closed` 模式下，這個屬性將返回 `null`。
- **樣式隔離**: 在 ShadowRoot 內部的樣式不會影響到主文檔，反之亦然，這使得開發者可以創建獨立且可重用的組件。

## 示例
以下是一個基本的使用示例：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>ShadowRoot 示例</title>
</head>
<body>
    <div id="myElement"></div>

    <script>
        const myElement = document.getElementById('myElement');
        const shadowRoot = myElement.attachShadow({ mode: 'open' });

        const div = document.createElement('div');
        div.textContent = '這是封裝在 ShadowRoot 中的內容！';
        shadowRoot.appendChild(div);

        const style = document.createElement('style');
        style.textContent = 'div { color: blue; }';
        shadowRoot.appendChild(style);
    </script>
</body>
</html>
```

在這個示例中，我們創建了一個新的 ShadowRoot 並添加了一些內容和樣式，這些樣式將不會影響到其他 DOM 元素。

## 解釋
- **常見問題**: 使用 ShadowRoot 時，開發者可能會遇到無法訪問 ShadowRoot 的情況，這通常是因為使用了 `closed` 模式。確保根據需要選擇正確的模式。
- **性能考量**: 雖然 Shadow DOM 提供了封裝和樣式隔離的優勢，但在性能上可能會有一定的開銷，特別是在創建大量組件時。

## 一句話總結
ShadowRoot 是 JavaScript 中用於創建封裝的 Web 組件 DOM 樹的介面，提供樣式和結構的獨立性。