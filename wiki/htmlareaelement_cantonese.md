<!--
Meta Description: # HTMLAreaElement：JavaScript 中的 HTML 區域元素 ## 概述 HTMLAreaElement 是一個代表 HTML `<area>` 標籤的介面，這個標籤通常用於定義圖像地圖中的可點擊區域。這個元素在 JavaScript 中的操作是非常重要的，特別是在處理用戶互動...
Meta Keywords: htmlareaelement, html, map, javascript, area
-->

# HTMLAreaElement：JavaScript 中的 HTML 區域元素

## 概述
HTMLAreaElement 是一個代表 HTML `<area>` 標籤的介面，這個標籤通常用於定義圖像地圖中的可點擊區域。這個元素在 JavaScript 中的操作是非常重要的，特別是在處理用戶互動和導航時。

## 文檔
### 目的
HTMLAreaElement 目的是讓開發者能夠以編程方式訪問和操作 HTML `<area>` 標籤的屬性和方法，進而提高網頁的互動性。

### 使用
HTMLAreaElement 是 HTML 的一部分，通常與 `<map>` 標籤搭配使用。這使得開發者可以創建可點擊的區域，並將它們連結到不同的 URL 或執行 JavaScript 函數。

#### 屬性
- `alt`: 定義區域的替代文本。
- `coords`: 定義區域的坐標。
- `href`: 定義點擊區域後的鏈接。
- `shape`: 定義區域的形狀（如 `rect`、`circle` 或 `poly`）。

#### 方法
HTMLAreaElement 除了擁有標準的 DOM 方法外，還包括一些特定的方法，如 `setAttribute()` 和 `getAttribute()`，用於操作屬性。

## 示例
以下是使用 HTMLAreaElement 的基本示例：

```html
<img src="image.jpg" usemap="#image-map">

<map name="image-map">
    <area target="" alt="Description" title="Description" href="http://example.com" coords="34,44,270,350" shape="rect">
</map>
```

在這個示例中，當用戶點擊圖像中的矩形區域時，將會導航到 `http://example.com`。

## 解釋
使用 HTMLAreaElement 時，開發者需要注意以下幾點：

1. **坐標系統**：在定義 `coords` 時，必須根據圖像的大小來正確設置坐標。如果坐標不正確，區域可能無法正確響應點擊事件。
   
2. **形狀定義**：確保在 `shape` 屬性中使用正確的值（`rect`、`circle`、`poly`），否則將無法呈現預期的效果。

3. **替代文本**：始終為 `alt` 屬性提供描述性文本，以提高可訪問性，這對於使用屏幕閱讀器的用戶至關重要。

## 一行總結
HTMLAreaElement 是用於操作 HTML `<area>` 標籤的 JavaScript 介面，方便開發者創建互動式圖像地圖。