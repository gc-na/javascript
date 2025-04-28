<!--
Meta Description: # getComputedStyle：JavaScript 中獲取元素計算樣式的功能 ## 概述 `getComputedStyle` 是一個 JavaScript 方法，用於獲取特定元素的最終計算樣式，這些樣式包括所有的 CSS 規則和樣式屬性，無論是內聯樣式還是外部樣式表。這對於需要在運行時獲取...
Meta Keywords: getcomputedstyle, javascript, element, const, css
-->

# getComputedStyle：JavaScript 中獲取元素計算樣式的功能

## 概述
`getComputedStyle` 是一個 JavaScript 方法，用於獲取特定元素的最終計算樣式，這些樣式包括所有的 CSS 規則和樣式屬性，無論是內聯樣式還是外部樣式表。這對於需要在運行時獲取元素的實際樣式的情境非常有用。

## 文檔
### 目的
`getComputedStyle` 主要用於獲取某個 DOM 元素的計算樣式，這些樣式是由瀏覽器在渲染該元素時計算出來的。這意味著即使某些樣式是通過 CSS 規則隱式設定的，`getComputedStyle` 也能獲取到它們的最終值。

### 使用方式
語法如下：
```javascript
window.getComputedStyle(element, pseudoElement);
```
- **element**：要獲取樣式的 DOM 元素。
- **pseudoElement**（可選）：一個字符串，表示要獲取的偽元素（例如 `::before` 或 `::after`），如果不需要，則可以省略。

返回值是一個 `CSSStyleDeclaration` 對象，該對象包含所有計算的 CSS 屬性及其值。

### 詳細說明
- `getComputedStyle` 只能用于 DOM 元素，不能用於其他對象。
- 返回的 CSS 屬性值通常是以像素為單位的，但某些屬性可能會返回不同的單位（例如顏色或百分比）。
- 這個方法會返回一個只讀的 CSSStyleDeclaration 對象，無法直接修改樣式。

## 示例
### 基本用法示例
```javascript
// 獲取元素
const element = document.getElementById('myElement');

// 獲取元素的計算樣式
const computedStyle = window.getComputedStyle(element);

// 獲取特定屬性值
const backgroundColor = computedStyle.backgroundColor;
console.log('背景顏色:', backgroundColor);
```

### 獲取偽元素樣式示例
```javascript
const element = document.getElementById('myElement');

// 獲取偽元素的樣式
const pseudoElementStyle = window.getComputedStyle(element, '::before');
const content = pseudoElementStyle.content;
console.log('偽元素內容:', content);
```

## 解釋
- **常見陷阱**：在使用 `getComputedStyle` 時，確保傳入的元素已經被添加到 DOM 中，否則可能會獲取到 `null` 或未定義的結果。
- **性能考量**：頻繁調用 `getComputedStyle` 可能會導致性能下降，特別是在動畫或重繪期間，應謹慎使用。
- **不同瀏覽器**：雖然大多數現代瀏覽器都支持 `getComputedStyle`，但在老舊的瀏覽器中可能會有兼容性問題，建議測試多個環境。

## 一句總結
`getComputedStyle` 是 JavaScript 中用來獲取元素最終計算樣式的有效方法。