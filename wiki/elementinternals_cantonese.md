<!--
Meta Description: # ElementInternals：JavaScript 中的元素內部屬性 ## 簡介 ElementInternals 是一個用於 Web 元素的 JavaScript 接口，允許開發者訪問和管理自定義元素的內部屬性，特別是在使用自定義元素和 Web 組件時，提供了更高的靈活性和控制能力。 ##...
Meta Keywords: elementinternals, javascript, web, mycustomelement, internals
-->

# ElementInternals：JavaScript 中的元素內部屬性

## 簡介
ElementInternals 是一個用於 Web 元素的 JavaScript 接口，允許開發者訪問和管理自定義元素的內部屬性，特別是在使用自定義元素和 Web 組件時，提供了更高的靈活性和控制能力。

## 文檔
ElementInternals 的主要目的是為了提升自定義元素的可訪問性和可用性。這個接口提供了一些屬性和方法，開發者可以通過它們來設置和獲取元素的內部狀態。

### 使用方法
要使用 ElementInternals，開發者需要在自定義元素的建構函數中調用 `attachInternals` 方法，這樣就可以獲取到 ElementInternals 的實例。

#### 主要屬性及方法：
- **`elementInternals`**: 返回當前元素的 ElementInternals 實例。
- **`setFormValue(value)`**: 設置表單的值。
- **`setValidity(validityState)`**: 設置元素的有效性狀態。
- **`reportValidity()`**: 報告當前的有效性狀態。

## 範例
以下是使用 ElementInternals 的基本範例：

```javascript
class MyCustomElement extends HTMLElement {
    constructor() {
        super();
        this.internals = this.attachInternals();
    }

    connectedCallback() {
        this.internals.setValidity({ valid: true });
        this.internals.setFormValue('Hello World');
    }
}

customElements.define('my-custom-element', MyCustomElement);
```

在該範例中，我們創建了一個自定義元素 `MyCustomElement`，並在其中使用 ElementInternals 的方法來設置有效性和表單值。

## 解釋
在使用 ElementInternals 時，開發者應注意以下常見問題：
- **不支持的瀏覽器**：ElementInternals 目前並不被所有瀏覽器完整支持，開發者應檢查相應的瀏覽器兼容性。
- **有效性狀態**：在設置有效性狀態時，必須確保所設置的狀態符合表單的狀態要求，否則可能會導致意外行為。

## 一句總結
ElementInternals 讓開發者能夠更好地控制自定義元素的內部狀態和有效性，提高了 Web 應用的可訪問性。