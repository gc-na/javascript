<!--
Meta Description: # HTMLMapElement 在 JavaScript 中的應用 ## 概述 HTMLMapElement 是一個在 JavaScript 中用來操作 HTML `<map>` 標籤的介面。它允許開發者以程式方式訪問和修改地圖的區域及其相關屬性，從而增強網頁的互動性。 ## 文檔 HTMLMap...
Meta Keywords: map, area, htmlmapelement, javascript, example
-->

# HTMLMapElement 在 JavaScript 中的應用

## 概述
HTMLMapElement 是一個在 JavaScript 中用來操作 HTML `<map>` 標籤的介面。它允許開發者以程式方式訪問和修改地圖的區域及其相關屬性，從而增強網頁的互動性。

## 文檔
HTMLMapElement 主要用於定義一個可互動的圖像地圖，這種地圖可以將圖片中的不同區域與特定的 URL 連結起來。這些區域通常是透過 `<area>` 標籤來定義的。使用 HTMLMapElement，開發者可以通過 JavaScript 來動態地控制這些區域的行為。

### 目的
- 提供對 `<map>` 標籤的程式化訪問。
- 能夠添加、修改或刪除地圖的區域。

### 使用方法
要使用 HTMLMapElement，首先需要在 HTML 文件中定義 `<map>` 標籤，然後使用 JavaScript 獲取這個元素。

```html
<img src="image.jpg" usemap="#image-map">
<map name="image-map">
    <area target="" alt="Description" title="Title" href="https://example.com" coords="34,44,270,350" shape="rect">
</map>
```

在 JavaScript 中，你可以這樣訪問和操作 HTMLMapElement：

```javascript
const map = document.querySelector('map[name="image-map"]');

// 獲取所有區域
const areas = map.getElementsByTagName('area');

// 修改第一個區域的 href 屬性
if (areas.length > 0) {
    areas[0].href = "https://new-url.com";
}
```

## 範例
以下是如何使用 HTMLMapElement 的基本範例：

```html
<img src="example.jpg" usemap="#example-map">
<map name="example-map">
    <area shape="rect" coords="34,44,270,350" href="https://example1.com" alt="Example 1">
    <area shape="circle" coords="377,300,44" href="https://example2.com" alt="Example 2">
</map>

<script>
    const map = document.querySelector('map[name="example-map"]');
    const areas = map.getElementsByTagName('area');

    for (let area of areas) {
        area.addEventListener('mouseover', () => {
            area.style.outline = "2px solid red"; // 鼠標懸停時添加邊框
        });
        area.addEventListener('mouseout', () => {
            area.style.outline = "none"; // 鼠標移出時移除邊框
        });
    }
</script>
```

## 解釋
使用 HTMLMapElement 時，開發者需要注意以下幾點：

1. **區域形狀**：`<area>` 標籤的 shape 屬性可以是 `rect`、`circle` 或 `poly`，每種形狀對應的 coords 屬性格式不同，必須正確設置。
2. **事件處理**：為區域添加事件時，確保事件處理器不會影響到其他區域的行為。
3. **瀏覽器兼容性**：部分舊版瀏覽器可能對 `<map>` 和 `<area>` 的支持不完全，建議進行測試以確保跨瀏覽器的兼容性。

## 一句總結
HTMLMapElement 使開發者能夠在 JavaScript 中以程式化方式操作 HTML 地圖，增強網頁互動性。