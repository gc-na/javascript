<!--
Meta Description: # JavaScript 中的「parent」概念 ## 概述 在 JavaScript 中，「parent」通常指的是一個元素或物件的上層結構，尤其是在處理 DOM（文檔物件模型）時。它能夠幫助開發者方便地訪問和操作父元素，從而進行更靈活的網頁互動。 ## 文件說明 「parent」在 JavaS...
Meta Keywords: parent, javascript, dom, child, parentelement
-->

# JavaScript 中的「parent」概念

## 概述
在 JavaScript 中，「parent」通常指的是一個元素或物件的上層結構，尤其是在處理 DOM（文檔物件模型）時。它能夠幫助開發者方便地訪問和操作父元素，從而進行更靈活的網頁互動。

## 文件說明
「parent」在 JavaScript 中主要涉及以下兩個方面：

1. **DOM 樹中的父元素**：使用 `parentNode` 或 `parentElement` 屬性來獲取某個 DOM 元素的父元素。這在操作 HTML 結構時非常有用，因為它可以讓開發者輕易地找到需要的元素進行修改或刪除。

2. **物件繼承中的父物件**：在物件導向編程中，JavaScript 使用原型鏈來實現繼承。子物件可以透過 `__proto__` 屬性訪問其父物件的屬性和方法。

### 用法
- **獲取 DOM 元素的父元素**：
  - `element.parentNode`：返回指定元素的父節點。
  - `element.parentElement`：返回指定元素的父元素。如果父元素是文檔節點，則返回 `null`。

- **獲取物件的父物件**：
  - `object.__proto__`：返回該物件的原型，即父物件。

## 範例
### 獲取 DOM 元素的父元素
```javascript
let childElement = document.getElementById("child");
let parentElement = childElement.parentNode; // 獲取父元素
console.log(parentElement.tagName); // 輸出父元素的標籤名稱
```

### 獲取物件的父物件
```javascript
function Parent() {
  this.name = "Parent";
}

function Child() {
  this.name = "Child";
}

Child.prototype = new Parent(); // 設定 Child 的原型為 Parent
let childInstance = new Child();
console.log(childInstance.__proto__.name); // 輸出 "Parent"
```

## 說明
在使用「parent」概念時，開發者需要注意以下幾點：

- 獲取 DOM 元素的父元素時，如果元素是根元素，`parentNode` 可能會返回 `document`，而 `parentElement` 則會返回 `null`。
- 在物件繼承中，使用 `__proto__` 雖然方便，但不被所有 JavaScript 開發者推薦，因為它不是正式的語言標準，建議使用 `Object.getPrototypeOf()` 來獲取父物件。
- 確保在操作 DOM 前文檔已完全加載，否則可能會導致 `null` 錯誤。

## 一行總結
「parent」在 JavaScript 中用於獲取元素的上層結構或物件的原型，對於 DOM 操作和物件導向編程至關重要。