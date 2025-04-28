<!--
Meta Description: # HTMLAreaElement：JavaScript 中的 HTML 區域元素 ## 簡介 HTMLAreaElement 是一個代表 HTML `<area>` 元素的接口，該元素通常用於定義圖像地圖中的可點擊區域。通過 JavaScript 操作 HTMLAreaElement，開發者可以動...
Meta Keywords: htmlareaelement, area, html, map, shape
-->

# HTMLAreaElement：JavaScript 中的 HTML 區域元素

## 簡介
HTMLAreaElement 是一個代表 HTML `<area>` 元素的接口，該元素通常用於定義圖像地圖中的可點擊區域。通過 JavaScript 操作 HTMLAreaElement，開發者可以動態改變網頁中的圖像地圖行為和樣式。

## 文件說明
HTMLAreaElement 接口是 Document Object Model (DOM) 的一部分，專門用於表示 HTML 中的 `<area>` 標籤。這些標籤用於定義一幅圖像中的可點擊區域，並可與 `<map>` 標籤配合使用。每個 `<area>` 元素可以設定不同的屬性，如 `href`、`shape` 和 `coords`，以控制用戶點擊後的行為。

### 主要屬性
- **href**: 指向用戶點擊後應導航的 URL。
- **shape**: 定義區域的形狀，常見的值有 `rect`、`circle` 和 `poly`。
- **coords**: 用於指定區域的坐標，具體格式根據 `shape` 的不同而不同。
- **alt**: 提供區域的替代文本，這對於無法顯示圖像時的輔助功能特別重要。

## 範例
以下是使用 HTMLAreaElement 的基本範例：

```html
<img src="example.jpg" usemap="#image-map">
<map name="image-map">
    <area target="" alt="範例區域" title="範例區域" href="https://www.example.com" coords="34,44,270,350" shape="rect">
</map>
```

在這個範例中，一幅圖像與一個圖像地圖相關聯，其中定義了一個矩形的可點擊區域。

## 解釋
使用 HTMLAreaElement 時需注意以下幾點：
- 確保 `<area>` 元素的 `coords` 屬性正確無誤，否則可能導致點擊行為不如預期。
- `shape` 屬性必須與 `coords` 屬性保持一致，否則可能無法正確顯示可點擊區域。
- 確保所有的 `<area>` 元素都包含 `href` 或 `alt` 屬性，以提高可訪問性。

## 總結
HTMLAreaElement 是一個關鍵的 JavaScript 介面，讓開發者能夠有效操作 HTML 中的圖像地圖區域，提升用戶互動體驗。