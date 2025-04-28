<!--
Meta Description: # JavaScript 中的 Proxy：全面指南 ## 概述 Proxy 是一種 JavaScript 內建的物件，可以讓你定義基本操作的自訂行為，如屬性存取、賦值、列舉等。這在建立可擴展的 API 和進行物件封裝時非常有用。 ## 文檔 ### 目的 Proxy 允許開發者創建一個代理物件，並...
Meta Keywords: proxy, target, javascript, handler, const
-->

# JavaScript 中的 Proxy：全面指南

## 概述
Proxy 是一種 JavaScript 內建的物件，可以讓你定義基本操作的自訂行為，如屬性存取、賦值、列舉等。這在建立可擴展的 API 和進行物件封裝時非常有用。

## 文檔
### 目的
Proxy 允許開發者創建一個代理物件，並定義如何處理對其目標物件的操作。這使得開發者可以攔截並自訂對物件的基本操作，進而增強物件的功能。

### 使用方法
要創建 Proxy，需使用 `new Proxy(target, handler)` 語法，其中：
- `target` 是要代理的原始物件。
- `handler` 是一個物件，定義了攔截操作的函數。

### 屬性
Proxy 提供了多種攔截器函數，以下是一些常用的攔截器：
- `get`：攔截屬性存取。
- `set`：攔截屬性賦值。
- `has`：攔截 `in` 運算符。
- `deleteProperty`：攔截刪除屬性。
- `apply`：攔截函數調用。
- `construct`：攔截建構函數調用。

### 例子
以下是 Proxy 的基本使用範例：

```javascript
// 定義目標物件
const target = {
    message: "Hello, World!"
};

// 定義處理器
const handler = {
    get: function(target, prop) {
        return prop in target ? target[prop] : "屬性不存在";
    }
};

// 創建 Proxy
const proxy = new Proxy(target, handler);

// 使用 Proxy
console.log(proxy.message); // 輸出: Hello, World!
console.log(proxy.nonExistentProp); // 輸出: 屬性不存在
```

## 解釋
### 常見陷阱與注意事項
1. **攔截時機**：Proxy 只會攔截透過代理物件進行的操作，對於直接操作目標物件的行為不會有影響。
2. **性能影響**：由於 Proxy 會攔截所有操作，可能會對性能造成影響，特別是在高頻操作的情況下。
3. **屬性描述符**：使用 Proxy 時，無法直接通過物件的屬性描述符來控制屬性的可寫性和可列舉性。

## 單行總結
Proxy 是一個強大的 JavaScript 特性，允許開發者自訂物件的基本操作行為，以增強功能和控制。