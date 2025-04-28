<!--
Meta Description: # DOMQuad：JavaScript 中的幾何矩形物件 ## 簡介 DOMQuad 是一個在 JavaScript 中用於處理元素的幾何形狀和位置的物件，主要用於獲取和描述元素在視窗中的位置和大小。 ## 文檔 DOMQuad 物件是由 `getClientRects()` 和 `getBoun...
Meta Keywords: domquad, rects, javascript, const, element
-->

# DOMQuad：JavaScript 中的幾何矩形物件

## 簡介
DOMQuad 是一個在 JavaScript 中用於處理元素的幾何形狀和位置的物件，主要用於獲取和描述元素在視窗中的位置和大小。

## 文檔
DOMQuad 物件是由 `getClientRects()` 和 `getBoundingClientRect()` 方法返回的，這些方法可以在 HTML 元素上調用，並提供該元素的邊界框和相應的四個邊界點（左上、右上、右下、左下）的座標。

### 目的
DOMQuad 的主要目的是為了提供一種方便的方式來獲取元素在視窗中的位置和大小，這對於許多需要精確定位的應用場景非常重要。

### 使用
要使用 DOMQuad，您可以通過以下方式取得：

```javascript
const element = document.querySelector('your-selector');
const rects = element.getClientRects();
```

這將返回一個 DOMRectList，您可以從中獲取每個 DOMRect（即 DOMQuad）。

### 詳細信息
DOMQuad 物件提供了以下屬性：
- `x`: 左上角的 x 坐標。
- `y`: 左上角的 y 坐標。
- `width`: 矩形的寬度。
- `height`: 矩形的高度。

這些屬性使得開發者能夠輕鬆地計算和操作元素的幾何信息。

## 範例
以下是一個簡單的示例，說明如何使用 DOMQuad 來獲取一個元素的幾何信息：

```javascript
const element = document.querySelector('.example');
const rects = element.getClientRects();

for (let i = 0; i < rects.length; i++) {
    console.log(`第 ${i + 1} 個矩形:`);
    console.log(`X: ${rects[i].x}, Y: ${rects[i].y}, 寬度: ${rects[i].width}, 高度: ${rects[i].height}`);
}
```

## 解釋
在使用 DOMQuad 時，有幾個常見的注意事項：
1. **多重矩形**：一個元素可以有多個矩形，特別是在使用 CSS 樣式（如邊框、內邊距）時，您可能會獲得多個 DOMRect。
2. **視圖變化**：當視窗大小改變時，元素的幾何信息也會隨之改變，因此要確保在適當的時機獲取信息，例如在窗口重繪後。
3. **跨瀏覽器行為**：不同的瀏覽器可能對 DOMQuad 的支持有細微差異，建議在主要瀏覽器中進行測試。

## 一句摘要
DOMQuad 是一種用於獲取和描述元素幾何位置的 JavaScript 物件，具有精確的邊界框資訊。