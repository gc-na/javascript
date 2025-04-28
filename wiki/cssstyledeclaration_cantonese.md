<!--
Meta Description: # CSSStyleDeclaration: JavaScript 中的 CSS 屬性操作 ## 概述 `CSSStyleDeclaration` 物件用於表示元素的 CSS 樣式聲明，允許 JavaScript 動態訪問和修改 HTML 元素的樣式。 ## 文檔 `CSSStyleDeclarat...
Meta Keywords: css, cssstyledeclaration, javascript, element, style
-->

# CSSStyleDeclaration: JavaScript 中的 CSS 屬性操作

## 概述
`CSSStyleDeclaration` 物件用於表示元素的 CSS 樣式聲明，允許 JavaScript 動態訪問和修改 HTML 元素的樣式。

## 文檔
`CSSStyleDeclaration` 是一個包含一組 CSS 屬性的物件。每個屬性都代表了一個 CSS 樣式，並可通過 JavaScript 進行操作。這些屬性可以直接通過 JavaScript 代碼進行訪問和修改，使得動態樣式更改變得簡單。

### 目的
`CSSStyleDeclaration` 的主要目的是讓開發者能夠以編程方式操縱 CSS 樣式，從而實現更靈活的網頁設計和交互。

### 使用
在 JavaScript 中，您可以通過 `element.style` 屬性獲取和修改某個 HTML 元素的 `CSSStyleDeclaration`。這樣，您可以直接對元素的樣式進行變更，而無需修改外部 CSS 文件。

### 詳細信息
- 每個屬性名稱都可以通過駝峰命名法訪問，例如 `backgroundColor` 對應於 CSS 的 `background-color`。
- 您可以使用 `setProperty` 方法來設置屬性，並指定屬性的名稱、值及優先級。
- 這個物件的屬性是動態的，對於任何樣式的改變都會立即生效。

## 示例
```javascript
// 獲取元素
let element = document.getElementById("myElement");

// 訪問樣式屬性
element.style.color = "red"; // 設置文本顏色為紅色
element.style.backgroundColor = "blue"; // 設置背景顏色為藍色

// 使用 setProperty 設置屬性
element.style.setProperty("font-size", "20px");
```

## 解釋
在使用 `CSSStyleDeclaration` 時，開發者應注意以下幾點：
- 確保屬性名稱正確，使用駝峰命名法。
- 當使用 `setProperty` 時，請注意第三個參數（優先級），如果未指定，默認為 `""`，這可能會導致意外的效果。
- 修改內聯樣式不會影響外部或內部樣式表，如果需要全局樣式變更，應考慮修改 CSS 文件。

## 單行總結
`CSSStyleDeclaration` 允許 JavaScript 動態訪問和修改 HTML 元素的 CSS 樣式。