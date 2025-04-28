<!--
Meta Description: # 自訂元素 (customElements) 在 JavaScript 中的應用 ## 摘要 自訂元素（customElements）是 Web Components 的一部分，允許開發者定義自己的 HTML 標籤，並為其提供行為。這使得創建可重用、封裝的組件變得容易，提高了網頁應用的可維護性和可...
Meta Keywords: html, customelements, 自訂元素, javascript, htmlelement
-->

# 自訂元素 (customElements) 在 JavaScript 中的應用

## 摘要
自訂元素（customElements）是 Web Components 的一部分，允許開發者定義自己的 HTML 標籤，並為其提供行為。這使得創建可重用、封裝的組件變得容易，提高了網頁應用的可維護性和可擴展性。

## 文檔
自訂元素 API 使得開發者可以創建自定義的 HTML 元素，這些元素可以在應用中重複使用。這個 API 主要由以下幾個部分組成：

1. **定義自訂元素**：
   使用 `customElements.define()` 方法來定義新的元素。這個方法需要兩個參數：元素的名稱（必須包含連字符）和一個類別，這個類別必須繼承自 `HTMLElement`。

   ```javascript
   class MyElement extends HTMLElement {
       constructor() {
           super();
           // 初始化代碼
       }
   }

   customElements.define('my-element', MyElement);
   ```

2. **使用自訂元素**：
   一旦定義了自訂元素，就可以在 HTML 中像使用內建元素一樣使用它：

   ```html
   <my-element></my-element>
   ```

3. **生命週期回調**：
   自訂元素提供了多個生命週期回調方法，例如 `connectedCallback()` 和 `disconnectedCallback()`，這些方法在元素被插入或移除 DOM 時自動調用。

   ```javascript
   class MyElement extends HTMLElement {
       connectedCallback() {
           this.innerHTML = '<p>自訂元素已連接到 DOM。</p>';
       }

       disconnectedCallback() {
           console.log('自訂元素已從 DOM 中移除。');
       }
   }
   ```

## 示例
以下是一個簡單的自訂元素範例：

```javascript
class HelloWorld extends HTMLElement {
    constructor() {
        super();
        this.attachShadow({ mode: 'open' });
        this.shadowRoot.innerHTML = `<p>你好，世界！</p>`;
    }
}

customElements.define('hello-world', HelloWorld);
```

在 HTML 中使用：

```html
<hello-world></hello-world>
```

## 解釋
在使用自訂元素時，開發者需要注意以下幾點：

- **名稱規範**：自訂元素的名稱必須包含一個連字符，例如 `my-element`，否則瀏覽器會拒絕註冊這個元素。
- **生命週期方法**：確保正確實現生命週期方法，以處理元素的創建和銷毀時的行為。
- **封裝**：使用 Shadow DOM 可以封裝樣式和行為，避免與全局 CSS 產生衝突。
- **瀏覽器支援**：雖然大多數現代瀏覽器都支援自訂元素，但在開發時仍需考慮兼容性，並可能需要使用 polyfills。

## 總結
自訂元素（customElements）是一個強大的 API，使開發者能夠創建可重用的 HTML 元素，提升網頁應用的可維護性和擴展性。