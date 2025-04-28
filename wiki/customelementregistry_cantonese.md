<!--
Meta Description: # CustomElementRegistry 在 JavaScript 中的應用 ## 概述 `CustomElementRegistry` 是一個 Web API，允許開發者註冊和管理自定義元素，這些元素是基於 Web Components 標準的。透過這個 API，開發者可以創建新的 HTML...
Meta Keywords: customelementregistry, element, html, name, javascript
-->

# CustomElementRegistry 在 JavaScript 中的應用

## 概述
`CustomElementRegistry` 是一個 Web API，允許開發者註冊和管理自定義元素，這些元素是基於 Web Components 標準的。透過這個 API，開發者可以創建新的 HTML 標籤，並為其定義行為和屬性。

## 文檔
`CustomElementRegistry` 的主要目的是為了讓開發者能夠創建可重用的自定義 HTML 元素。在 JavaScript 中，使用 `customElements` 對象來訪問 `CustomElementRegistry` 的功能。這個對象提供了兩個主要方法：`define` 和 `get`。

### 方法
1. **define(name, constructor[, options])**
   - **參數**：
     - `name`：自定義元素的名稱，必須包含一個連字號（例如 `my-element`）。
     - `constructor`：一個類，該類必須繼承自 `HTMLElement`。
     - `options`（可選）：一個選項對象，包含元素的生命周期回調。
   - **用途**：註冊一個新的自定義元素。

2. **get(name)**
   - **參數**：
     - `name`：要獲取的自定義元素的名稱。
   - **用途**：返回已註冊的自定義元素的建構函數，如果未找到則返回 `undefined`。

## 示例
### 基本用法
以下是如何使用 `CustomElementRegistry` 註冊一個簡單的自定義元素的範例：

```javascript
class MyElement extends HTMLElement {
    constructor() {
        super();
        this.attachShadow({ mode: 'open' }).innerHTML = `<p>Hello, Custom Element!</p>`;
    }
}

customElements.define('my-element', MyElement);

// 使用自定義元素
const element = document.createElement('my-element');
document.body.appendChild(element);
```

## 解釋
使用 `CustomElementRegistry` 時，開發者應注意以下幾點：
- 自定義元素的名稱必須包含一個連字號，以避免與現有的 HTML 元素名稱衝突。
- 如果嘗試重複註冊同一個元素名稱，將會拋出錯誤。
- 在使用 `get` 方法獲取元素時，必須確認元素已經被註冊，否則會返回 `undefined`。

## 總結
`CustomElementRegistry` 提供了一種方便的方式來創建和管理自定義 HTML 元素，從而增強了 Web 應用的可重用性和可維護性。