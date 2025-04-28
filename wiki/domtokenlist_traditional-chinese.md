<!--
Meta Description: # DOMTokenList：JavaScript 的強大工具來操作 CSS 類別 ## 摘要 DOMTokenList 是一個 JavaScript 物件，用於操作 HTML 元素的類別屬性，提供了一種方便的方式來添加、刪除和管理元素的 CSS 類別。 ## 文件說明 DOMTokenList 是...
Meta Keywords: element, domtokenlist, javascript, classlist, active
-->

# DOMTokenList：JavaScript 的強大工具來操作 CSS 類別

## 摘要
DOMTokenList 是一個 JavaScript 物件，用於操作 HTML 元素的類別屬性，提供了一種方便的方式來添加、刪除和管理元素的 CSS 類別。

## 文件說明
DOMTokenList 是一個代表一組空白分隔的字串的集合，特別用於管理元素的類別屬性。它提供了多種方法來操作這些類別，包括 `add()`、`remove()`、`toggle()` 和 `contains()`。這使得對 DOM 元素的樣式進行動態更改變得簡單而高效。

### 目的
DOMTokenList 主要用於：
- 動態添加或刪除 CSS 類別來改變元素的樣式。
- 檢查一個元素是否具有特定的類別。
- 切換類別以應對不同的狀態，如開關效果等。

### 使用方法
DOMTokenList 通常通過 `classList` 屬性獲取。以下是一些常用方法：

- **add(className)**：將指定的類別添加到元素中。
- **remove(className)**：從元素中刪除指定的類別。
- **toggle(className)**：如果存在則刪除，否則添加指定的類別。
- **contains(className)**：檢查元素是否擁有指定的類別。

## 範例
### 1. 添加類別
```javascript
const element = document.getElementById('myElement');
element.classList.add('active');
```

### 2. 刪除類別
```javascript
const element = document.getElementById('myElement');
element.classList.remove('active');
```

### 3. 切換類別
```javascript
const element = document.getElementById('myElement');
element.classList.toggle('active');
```

### 4. 檢查類別
```javascript
const element = document.getElementById('myElement');
if (element.classList.contains('active')) {
    console.log('Element is active');
} else {
    console.log('Element is not active');
}
```

## 解釋
在使用 DOMTokenList 時，開發者可能會遇到一些常見的陷阱：
- **類別名稱的重複**：使用 `add()` 方法時，如果嘗試添加一個已經存在的類別，則不會報錯，但也不會有任何效果。
- **無法直接使用 `classList`**：需要確保所操作的元素已經存在於 DOM 中，否則會報錯。
- **不支持 IE**：某些舊版瀏覽器（如 IE10及更早版本）不支持 `classList`，這在進行跨瀏覽器開發時需要注意。

## 總結
DOMTokenList 是一個強大的 JavaScript 物件，提供了靈活的方式來操作 HTML 元素的 CSS 類別，適合用於動態樣式管理和狀態切換。