<!--
Meta Description: # ShadowRoot：JavaScript 中的影子根 ## 概要 在 JavaScript 中，`ShadowRoot` 是 Web Components 的一部分，允許開發者創建封閉的 DOM 樹，從而為應用程式的組件提供樣式和行為的隔離。 ## 文件說明 `ShadowRoot` 是一種特...
Meta Keywords: dom, shadowroot, javascript, open, closed
-->

# ShadowRoot：JavaScript 中的影子根

## 概要
在 JavaScript 中，`ShadowRoot` 是 Web Components 的一部分，允許開發者創建封閉的 DOM 樹，從而為應用程式的組件提供樣式和行為的隔離。

## 文件說明
`ShadowRoot` 是一種特殊的 DOM 節點，用於創建影子 DOM。影子 DOM 使開發者能夠隱藏組件的內部結構，從而避免樣式衝突和 JavaScript 變數的範圍污染。這對於構建可重用的 UI 組件非常有用。

### 目的
`ShadowRoot` 的主要目的是提供一種封裝機制，使得組件內部的樣式和行為不會影響到頁面上的其他部分。

### 用法
要使用 `ShadowRoot`，需要首先創建一個包含影子 DOM 的元素。可以通過 `attachShadow` 方法來附加影子根。以下是其基本語法：

```javascript
let shadowRoot = element.attachShadow({ mode: 'open' | 'closed' });
```

- `mode`: 指定影子 DOM 的可訪問性，`open` 允許外部訪問影子 DOM，而 `closed` 則不允許。

## 範例
以下是使用 `ShadowRoot` 的簡單範例：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ShadowRoot 範例</title>
</head>
<body>
    <div id="myElement"></div>

    <script>
        const myElement = document.getElementById('myElement');

        // 附加影子根
        const shadowRoot = myElement.attachShadow({ mode: 'open' });

        // 在影子 DOM 中創建內容
        const para = document.createElement('p');
        para.textContent = '這是影子 DOM 中的段落！';
        shadowRoot.appendChild(para);

        // 添加樣式
        const style = document.createElement('style');
        style.textContent = 'p { color: blue; }';
        shadowRoot.appendChild(style);
    </script>
</body>
</html>
```

在此範例中，我們創建了一個包含段落的影子 DOM，並且設置了段落的顏色為藍色。

## 解釋
在使用 `ShadowRoot` 時，有幾個常見的陷阱：

1. **樣式隔離**：影子 DOM 中的樣式不會影響到主文檔的樣式，反之亦然。因此，如果需要在影子 DOM 中使用全局樣式，可能需要手動引入或複製。

2. **訪問性**：選擇 `open` 或 `closed` 模式會影響外部訪問影子 DOM 的能力。在 `closed` 模式下，無法通過 `element.shadowRoot` 訪問影子 DOM。

3. **性能考量**：雖然影子 DOM 提供了封裝性，但過度使用也可能對性能造成影響，特別是在大型應用中。

## 一句總結
`ShadowRoot` 是 JavaScript 中用於創建封閉和可重用 UI 組件的關鍵技術，使開發者能夠有效地隔離樣式和行為。