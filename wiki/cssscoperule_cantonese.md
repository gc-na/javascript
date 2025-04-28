<!--
Meta Description: # CSSScopeRule：JavaScript 中的 CSS 範圍規則 ## 概述 CSSScopeRule 是一種與 JavaScript 相關的 CSS 規則，旨在為特定範圍內的樣式提供隔離。它通常在使用 Shadow DOM 或 CSS 模組化技術時使用，能夠有效控制樣式的應用範圍，避免樣...
Meta Keywords: cssscoperule, shadow, javascript, const, document
-->

# CSSScopeRule：JavaScript 中的 CSS 範圍規則

## 概述
CSSScopeRule 是一種與 JavaScript 相關的 CSS 規則，旨在為特定範圍內的樣式提供隔離。它通常在使用 Shadow DOM 或 CSS 模組化技術時使用，能夠有效控制樣式的應用範圍，避免樣式沖突。

## 文檔
### 目的
CSSScopeRule 的主要目的是確保在複雜的應用程式中，樣式不會因為不同組件之間的重疊而產生混亂。這使得開發人員能夠創建可重用的組件，並保證每個組件的樣式不會影響其他組件。

### 使用
在 JavaScript 中，CSSScopeRule 通常與 Web Components 和 Shadow DOM 一起使用。當創建一個 Shadow Root 時，可以將 CSSScopeRule 應用於該範圍，從而限制樣式的影響範圍。

```javascript
const shadowHost = document.createElement('div');
const shadowRoot = shadowHost.attachShadow({ mode: 'open' });

const style = document.createElement('style');
style.textContent = `
  :host {
    display: block;
    background-color: lightblue;
  }
  p {
    color: darkblue;
  }
`;

shadowRoot.appendChild(style);
shadowRoot.innerHTML += '<p>這是一個範圍樣式的範例</p>';
document.body.appendChild(shadowHost);
```

在這個例子中，`style` 標籤中的 CSS 只會應用於 `shadowRoot` 內的元素，而不會影響到主文檔中的樣式。

## 示例
### 基本使用範例
以下是一個基本的用法範例，展示如何使用 CSSScopeRule 來隔離樣式：

```javascript
const container = document.createElement('div');
const shadow = container.attachShadow({ mode: 'open' });

const scopedStyle = document.createElement('style');
scopedStyle.textContent = `
  h1 {
    color: red;
  }
`;

shadow.appendChild(scopedStyle);
shadow.innerHTML += '<h1>這是範圍內的標題</h1>';
document.body.appendChild(container);
```

在這個範例中，只有在 `shadow` 內的 `h1` 標題會顯示為紅色。

## 解釋
### 常見陷阱
1. **樣式繼承問題**：使用 CSSScopeRule 時，必須了解樣式的繼承規則。某些屬性如 `color` 和 `font-size` 會被繼承，可能會導致意想不到的效果。
2. **性能問題**：過多的範圍樣式可能會影響性能，因此應根據需要合理使用。
3. **兼容性**：在某些舊版瀏覽器中，Shadow DOM 和 CSSScopeRule 可能不受支持，需注意兼容性問題。

### 額外說明
CSSScopeRule 的使用可以提升應用的可維護性和可重用性。隨著 Web Components 的普及，這一特性變得越來越重要。

## 一句話總結
CSSScopeRule 讓開發人員能夠在 JavaScript 中有效地隔離樣式，避免不同組件之間的樣式沖突。