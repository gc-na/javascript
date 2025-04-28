<!--
Meta Description: # Attr：JavaScript 中的屬性操作 ## Synopsis 在 JavaScript 中，`Attr` 是用於操作和獲取 HTML 元素屬性的功能，讓開發者能夠輕鬆地讀取和修改 DOM 元素的屬性值。 ## Documentation `Attr` 是一種方法，用於獲取或設置 HTML...
Meta Keywords: element, attr, javascript, html, getattribute
-->

# Attr：JavaScript 中的屬性操作

## Synopsis
在 JavaScript 中，`Attr` 是用於操作和獲取 HTML 元素屬性的功能，讓開發者能夠輕鬆地讀取和修改 DOM 元素的屬性值。

## Documentation
`Attr` 是一種方法，用於獲取或設置 HTML 元素的屬性。這些屬性包括標籤中的屬性（如 `class`、`id` 和自定義屬性），使開發者能夠操作網頁元素。`Attr` 方法的典型使用方式是通過 `Element` 物件來訪問。

### 使用方法
- **獲取屬性**: 使用 `element.getAttribute(attributeName)` 方法來獲取指定屬性的值。
- **設置屬性**: 使用 `element.setAttribute(attributeName, value)` 方法來設置指定屬性的值。
- **移除屬性**: 使用 `element.removeAttribute(attributeName)` 方法來移除指定的屬性。

### 參數
- `attributeName`：想要訪問或更改的屬性名稱，必須是字符串格式。
- `value`：要設置的屬性值，必須是字符串格式。

## Examples
### 獲取屬性值
```javascript
const element = document.querySelector('#myElement');
const classValue = element.getAttribute('class');
console.log(classValue); // 輸出：元素的 class 名稱
```

### 設置屬性值
```javascript
const element = document.querySelector('#myElement');
element.setAttribute('title', '這是一個提示');
```

### 移除屬性
```javascript
const element = document.querySelector('#myElement');
element.removeAttribute('disabled');
```

## Explanation
在使用 `Attr` 時，開發者可能會遇到以下常見問題：
- **大小寫敏感**：屬性名稱是大小寫敏感的，因此必須確保所使用的名稱正確。
- **非標準屬性**：對於非標準屬性（如自定義屬性），需要以 `data-*` 格式命名，如 `data-custom`，並通過 `getAttribute('data-custom')` 獲取。
- **屬性與 DOM 屬性**：注意 `getAttribute` 和 `element.property` 之間的區別，前者獲取的是 HTML 標籤中的屬性值，後者則是 DOM 物件中的屬性值。

## One Line Summary
`Attr` 方法是 JavaScript 中用於操作和獲取 HTML 元素屬性的有效工具。