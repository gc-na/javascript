<!--
Meta Description: # DOMRectReadOnly: JavaScript 中的不可變矩形物件 ## 簡介 `DOMRectReadOnly` 是一個表示矩形區域的物件，主要用於獲取元素的大小和位置信息。它是 `DOMRect` 的只讀版本，提供多個屬性，可以讓開發者輕鬆地獲取和使用元素的幾何資訊。 ## 文檔 `...
Meta Keywords: domrectreadonly, rect, console, log, javascript
-->

# DOMRectReadOnly: JavaScript 中的不可變矩形物件

## 簡介
`DOMRectReadOnly` 是一個表示矩形區域的物件，主要用於獲取元素的大小和位置信息。它是 `DOMRect` 的只讀版本，提供多個屬性，可以讓開發者輕鬆地獲取和使用元素的幾何資訊。

## 文檔
`DOMRectReadOnly` 是一個內建的 JavaScript 物件，主要用於表示一個矩形的邊界，並且不允許其屬性被修改。這是一個非常有用的工具，特別是在進行網頁布局和碰撞檢測時。

### 目的
`DOMRectReadOnly` 的主要目的在於提供一個簡單的方式來獲取矩形的尺寸和位置。這對於處理 CSS 動畫、事件偵測以及繪製圖形等情況非常重要。

### 使用方法
`DOMRectReadOnly` 主要是由其他 API 返回的，如 `getBoundingClientRect()` 方法。當你調用這些方法時，它們會返回一個 `DOMRectReadOnly` 物件，讓你可以訪問其屬性。

### 屬性
- `x`: 矩形的左上角 x 坐標。
- `y`: 矩形的左上角 y 坐標。
- `width`: 矩形的寬度。
- `height`: 矩形的高度。
- `top`: 矩形的上邊界。
- `right`: 矩形的右邊界。
- `bottom`: 矩形的下邊界。
- `left`: 矩形的左邊界。

## 範例
以下是一些使用 `DOMRectReadOnly` 的基本範例：

### 獲取元素的矩形
```javascript
const element = document.getElementById("myElement");
const rect = element.getBoundingClientRect();

console.log(`元素的位置: (${rect.x}, ${rect.y})`);
console.log(`元素的寬度: ${rect.width}`);
console.log(`元素的高度: ${rect.height}`);
```

### 獲取窗口的大小
```javascript
const rect = document.documentElement.getBoundingClientRect();
console.log(`視窗的寬度: ${rect.width}`);
console.log(`視窗的高度: ${rect.height}`);
```

## 解釋
使用 `DOMRectReadOnly` 時，有幾個常見的陷阱和注意事項：
- `DOMRectReadOnly` 物件是不可變的，因此你無法更改其屬性。如果需要改變矩形的大小或位置，必須重新獲取。
- 在一些情況下，獲取矩形信息的時機可能會影響結果，例如在 DOM 更新或動畫過程中。

## 一句總結
`DOMRectReadOnly` 是一個只讀矩形物件，用於表示和獲取 HTML 元素的幾何屬性，對於網頁開發至關重要。