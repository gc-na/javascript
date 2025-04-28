<!--
Meta Description: # JavaScript Proxy: 深入了解 JavaScript 的代理物件 ## 概述 JavaScript 的 Proxy 物件允許你創建一個代理來攔截和自定義對目標物件的基本操作，如屬性查詢、賦值、枚舉、函數調用等。 ## 文檔 ### 目的 Proxy 是 JavaScript 的一個...
Meta Keywords: proxy, target, const, property, javascript
-->

# JavaScript Proxy: 深入了解 JavaScript 的代理物件

## 概述
JavaScript 的 Proxy 物件允許你創建一個代理來攔截和自定義對目標物件的基本操作，如屬性查詢、賦值、枚舉、函數調用等。

## 文檔
### 目的
Proxy 是 JavaScript 的一個強大特性，主要用於提供對物件的控制和擴展能力。這可以幫助開發者在許多情況下進行數據驗證、數據綁定或追蹤操作。

### 用法
要創建一個 Proxy，你需要兩個參數：目標物件和一個處理器物件。處理器物件包含了一組攔截器，用於定義如何處理對目標物件的操作。

```javascript
const target = {};
const handler = {
    get: function(target, property) {
        return property in target ? target[property] : '屬性不存在';
    }
};

const proxy = new Proxy(target, handler);
```

### 詳細說明
- **目標物件**: 你想要監控或修改的原始物件。
- **處理器物件**: 包含各種攔截方法，如 `get`, `set`, `has`, `deleteProperty` 等，這些方法會在對目標物件進行相應操作時被調用。

## 示例
### 基本用法示例
```javascript
const target = { message: 'Hello, world!' };
const handler = {
    get: function(target, property) {
        return property in target ? target[property] : '屬性不存在';
    }
};

const proxy = new Proxy(target, handler);
console.log(proxy.message); // 輸出: "Hello, world!"
console.log(proxy.nonExistent); // 輸出: "屬性不存在"
```

### 攔截設置操作
```javascript
const target = {};
const handler = {
    set: function(target, property, value) {
        console.log(`設置 ${property} 為 ${value}`);
        target[property] = value;
        return true;
    }
};

const proxy = new Proxy(target, handler);
proxy.name = 'Alice'; // 輸出: "設置 name 為 Alice"
console.log(proxy.name); // 輸出: "Alice"
```

## 解釋
- **常見陷阱**: 在使用 Proxy 時，如果不小心會導致無限遞迴，比如在 `get` 或 `set` 方法中直接訪問原始目標物件的屬性。
- **性能考量**: 使用 Proxy 可能會影響性能，特別是當攔截器處理大量操作時。
- **不支持的操作**: 並不是所有的操作都可以被攔截，某些內建操作如 `instanceof` 不會觸發 Proxy。

## 一句總結
JavaScript 的 Proxy 物件為開發者提供了一種靈活的方式來攔截和自定義對物件的操作，增強了物件的可控性和擴展性。