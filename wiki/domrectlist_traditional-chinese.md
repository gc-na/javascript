<!--
Meta Description: # DOMRectList 在 JavaScript 中的應用 ## 簡介 `DOMRectList` 是一個在 JavaScript 中用來表示一組矩形（`DOMRect`）的集合的物件。這個物件通常在處理元素的邊界框或視口時使用，對於進行幾何計算和處理非常重要。 ## 文檔 `DOMRectLi...
Meta Keywords: domrectlist, rect, getclientrects, const, element
-->

# DOMRectList 在 JavaScript 中的應用

## 簡介
`DOMRectList` 是一個在 JavaScript 中用來表示一組矩形（`DOMRect`）的集合的物件。這個物件通常在處理元素的邊界框或視口時使用，對於進行幾何計算和處理非常重要。

## 文檔
`DOMRectList` 是 `DOMRect` 物件的集合，`DOMRect` 表示一個矩形的大小和位置。當我們需要獲取多個元素的邊界信息時，`DOMRectList` 提供了一個方便的方式來管理這些信息。它可以通過一些 API 獲取，比如 `getClientRects()` 和 `getBoundingClientRect()`。

### 用法
`DOMRectList` 通常是從 `getClientRects()` 方法中獲得。這個方法返回一個 `DOMRectList` 物件，包含了元素的所有可見矩形。以下是使用 `getClientRects()` 的基本示例：

```javascript
const element = document.getElementById('myElement');
const rects = element.getClientRects();

for (let rect of rects) {
    console.log(`矩形位置: (${rect.x}, ${rect.y}), 寬度: ${rect.width}, 高度: ${rect.height}`);
}
```

## 例子
### 基本用法
假設我們有一個 HTML 元素，我們想要獲取其邊界矩形信息：

```html
<div id="myElement" style="width: 200px; height: 100px; border: 1px solid black;"></div>
<script>
    const element = document.getElementById('myElement');
    const rectList = element.getClientRects();

    console.log(rectList.length); // 輸出矩形的數量

    for (let rect of rectList) {
        console.log(`X: ${rect.x}, Y: ${rect.y}, Width: ${rect.width}, Height: ${rect.height}`);
    }
</script>
```

### 荪效果
在存在多個可見矩形的情況下，例如當元素有多個邊框或陰影時，`DOMRectList` 允許我們獲取所有這些矩形信息：

```javascript
const element = document.getElementById('myElement');
const rects = element.getClientRects();

if (rects.length > 0) {
    console.log(`該元素有 ${rects.length} 個可見矩形`);
}
```

## 解釋
在使用 `DOMRectList` 時，有幾個常見的陷阱需要注意：
1. **不可變性**：`DOMRectList` 物件是只讀的，不能直接修改其中的矩形。
2. **矩形數量**：當元素被隱藏或不在視口內時，`getClientRects()` 會返回空的 `DOMRectList`，這可能會導致意外行為。
3. **複雜元素**：對於複雜的元素（如包含浮動元素或內嵌元素的容器），返回的矩形數量可能會超出預期。

## 一行總結
`DOMRectList` 是 JavaScript 中用來表示一組 `DOMRect` 矩形的集合，方便開發者進行幾何計算和元素邊界處理。