<!--
Meta Description: # 自訂元素註冊表（CustomElementRegistry）在 JavaScript 中的應用 ## 簡介 自訂元素註冊表（CustomElementRegistry）是 JavaScript 中用於定義和管理自訂 HTML 元素的接口。它使開發者能夠創建可重用的組件，提升網頁應用的可維護性和可...
Meta Keywords: javascript, hello, world, customelementregistry, html
-->

# 自訂元素註冊表（CustomElementRegistry）在 JavaScript 中的應用

## 簡介
自訂元素註冊表（CustomElementRegistry）是 JavaScript 中用於定義和管理自訂 HTML 元素的接口。它使開發者能夠創建可重用的組件，提升網頁應用的可維護性和可擴展性。

## 文檔
### 目的
自訂元素註冊表的主要目的是允許開發者定義自訂元素，這些元素可以像原生 HTML 元素一樣使用。這是 Web Components 標準的一部分，提供了封裝、重用和組合的能力。

### 使用方式
`CustomElementRegistry` 主要有兩個方法：
1. `define`: 定義一個新的自訂元素。
2. `get`: 獲取已定義的自訂元素。

#### 定義自訂元素
要定義一個自訂元素，需要使用 `define` 方法並提供元素名稱和一個類別。元素名稱必須包含至少一個連字符（-）以保證與內建元素的區別。

```javascript
class MyElement extends HTMLElement {
    constructor() {
        super();
        // 初始化代碼
    }
}

customElements.define('my-element', MyElement);
```

#### 獲取自訂元素
使用 `get` 方法可以檢查一個元素是否已經被定義。

```javascript
let elementClass = customElements.get('my-element');
console.log(elementClass); // 輸出 MyElement 類別
```

## 範例
以下是一個簡單的自訂元素範例：

```javascript
class HelloWorld extends HTMLElement {
    constructor() {
        super();
        this.attachShadow({ mode: 'open' }).innerHTML = '<p>Hello, World!</p>';
    }
}

customElements.define('hello-world', HelloWorld);

// 在 HTML 中使用自訂元素
document.body.innerHTML += '<hello-world></hello-world>';
```

這個範例中，我們創建了一個名為 `hello-world` 的自訂元素，並在頁面中顯示 "Hello, World!"。

## 解釋
### 常見問題
- **元素名稱要求**: 自訂元素的名稱必須包含至少一個連字符，否則將會拋出錯誤。
- **自訂元素的生命週期**: 自訂元素有自己的生命週期方法，例如 `connectedCallback` 和 `disconnectedCallback`，用於處理元素添加或移除時的邏輯。
  
### 注意事項
- **瀏覽器支援**: 大多數現代瀏覽器都支援自訂元素，但在使用之前最好檢查瀏覽器的兼容性。
- **重新定義元素**: 一旦元素被定義，就無法再次定義相同名稱的元素。若需更改定義，必須先使用 `disconnectedCallback` 移除所有實例。

## 一句話總結
自訂元素註冊表（CustomElementRegistry）允許開發者在 JavaScript 中定義和管理自訂 HTML 元素，提升網頁應用的可重用性和維護性。