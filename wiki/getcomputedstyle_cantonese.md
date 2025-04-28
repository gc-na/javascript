<!--
Meta Description: # 使用 JavaScript 獲取元素計算樣式的 getComputedStyle ## 簡介 `getComputedStyle` 是一個 JavaScript 方法，允許開發者獲取元素的計算樣式，包括所有應用於該元素的樣式（無論是內聯樣式、外部樣式表還是瀏覽器的默認樣式）。 ## 文檔 ###...
Meta Keywords: getcomputedstyle, javascript, style, const, element
-->

# 使用 JavaScript 獲取元素計算樣式的 getComputedStyle

## 簡介
`getComputedStyle` 是一個 JavaScript 方法，允許開發者獲取元素的計算樣式，包括所有應用於該元素的樣式（無論是內聯樣式、外部樣式表還是瀏覽器的默認樣式）。

## 文檔
### 目的
`getComputedStyle` 用於獲取一個 DOM 元素的最終計算樣式，這對於需要根據元素的顯示狀態進行操作的情況非常有用。

### 使用方式
語法如下：

```javascript
const style = getComputedStyle(element, pseudoElement);
```

- `element`: 目標 DOM 元素。
- `pseudoElement`（可選）：要獲取樣式的偽元素（例如 `::before` 或 `::after`）。如果不需要偽元素，可以傳入 `null`。

### 詳細說明
`getComputedStyle` 返回一個包含所有計算樣式的 CSSStyleDeclaration 對象。這個對象是只讀的，意味著你不能直接修改樣式。你可以使用該對象的屬性來獲取特定的樣式值，例如 `style.width`、`style.height`、`style.color` 等。

例如：

```javascript
const element = document.querySelector('.my-element');
const style = getComputedStyle(element);
console.log(style.color); // 獲取元素的文字顏色
```

## 示例
### 基本使用示例
```javascript
// 獲取一個 div 元素的背景顏色
const divElement = document.getElementById('myDiv');
const computedStyle = getComputedStyle(divElement);
console.log(computedStyle.backgroundColor);
```

### 獲取偽元素的樣式
```javascript
// 獲取一個元素的 :before 偽元素的內容樣式
const pseudoElementStyle = getComputedStyle(divElement, '::before');
console.log(pseudoElementStyle.content);
```

## 解釋
在使用 `getComputedStyle` 時，有一些常見的陷阱需要注意：

1. **計算樣式的延遲**：在某些情況下，當元素尚未顯示時，獲取的樣式可能不正確。因此，在 DOM 加載完成後使用此方法會更可靠。
   
2. **只讀屬性**：返回的 CSSStyleDeclaration 對象是只讀的，不能直接修改。如果需要更改樣式，需使用 `element.style` 進行更改。

3. **不同的瀏覽器差異**：雖然 `getComputedStyle` 在大多數現代瀏覽器中表現一致，但某些屬性的返回值可能會因瀏覽器而異。

## 一句總結
`getComputedStyle` 是一個強大的 JavaScript 方法，用於獲取 DOM 元素的最終計算樣式，對於進行樣式檢查和動態樣式調整非常有用。