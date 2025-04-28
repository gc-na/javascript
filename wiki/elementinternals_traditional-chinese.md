<!--
Meta Description: # ElementInternals: JavaScript 中的元素內部 ## 概述 `ElementInternals` 是一個 JavaScript 的 Web API，主要用於自定義元素的內部狀態管理，特別是在自定義元素（Custom Elements）中。它提供了一組方法來處理元素的屬性和...
Meta Keywords: elementinternals, input, javascript, attachinternals, internals
-->

# ElementInternals: JavaScript 中的元素內部

## 概述
`ElementInternals` 是一個 JavaScript 的 Web API，主要用於自定義元素的內部狀態管理，特別是在自定義元素（Custom Elements）中。它提供了一組方法來處理元素的屬性和狀態，允許開發者以更靈活的方式來操作和管理元素的行為和外觀。

## 文檔
### 目的
`ElementInternals` 的主要目的在於讓開發者能夠更好地管理和操作自定義元素的內部狀態。它提供 API 來存取和操控自定義元件的屬性、狀態，以及與這些元件相關的其他功能。

### 使用方法
要使用 `ElementInternals`，你首先需要創建一個自定義元素，然後可以使用 `attachInternals` 方法來獲取對應的 `ElementInternals` 實例。這個實例提供了多種方法來管理元素的內部狀態。

#### 基本用法
1. 定義自定義元素：
   ```javascript
   class MyCustomElement extends HTMLElement {
       constructor() {
           super();
           this.internals = this.attachInternals();
       }
   }
   customElements.define('my-custom-element', MyCustomElement);
   ```

2. 使用 `ElementInternals` 方法：
   ```javascript
   class MyCustomElement extends HTMLElement {
       constructor() {
           super();
           this.internals = this.attachInternals();
       }

       connectedCallback() {
           this.internals.setFormValue('Some value');
           console.log(this.internals.form); // 獲取元素的表單
       }
   }
   ```

### 詳細說明
`ElementInternals` 提供了以下幾個重要的方法：
- `attachInternals()`：將元素與一個 `ElementInternals` 實例關聯。
- `setFormValue(value)`：設置元素的表單值。
- `getFormValue()`：獲取當前的表單值。
- `setValidity(validityState)`：設置該元素的有效性狀態，用於表單驗證。
- `reportValidity()`：檢查元素的有效性並返回結果。

這些方法可以幫助開發者更精確地控制自定義元素的行為，特別是在表單處理和驗證方面。

## 範例
以下是使用 `ElementInternals` 的簡單範例：

```javascript
class MyCustomInput extends HTMLElement {
    constructor() {
        super();
        this.internals = this.attachInternals();
        this.input = document.createElement('input');
        this.appendChild(this.input);
    }

    connectedCallback() {
        this.input.addEventListener('input', () => {
            this.internals.setFormValue(this.input.value);
        });
    }
}

customElements.define('my-custom-input', MyCustomInput);
```

在這個範例中，自定義的 `my-custom-input` 元素將會自動管理其內部的表單值。

## 說明
使用 `ElementInternals` 時需要注意以下幾點：
- 確保在自定義元素的構造函數中調用 `attachInternals()` 方法，否則無法獲取 `ElementInternals` 實例。
- `ElementInternals` 的方法在某些情況下可能不會立即生效，特別是在與表單相關的操作中，建議在適當的事件中使用。
- 當處理表單驗證時，務必設置正確的有效性狀態，以確保用戶獲得正確的反饋。

## 一句總結
`ElementInternals` 是一個強大的 API，為 JavaScript 自定義元素提供了靈活的內部狀態管理功能。