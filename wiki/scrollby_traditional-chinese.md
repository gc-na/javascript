<!--
Meta Description: # scrollBy：JavaScript 中的滾動方法 ## 摘要 `scrollBy` 是一個用於在網頁中滾動視窗的 JavaScript 方法，允許開發者根據指定的水平和垂直偏移量來控制內容的滾動。 ## 文件說明 `scrollBy` 方法屬於瀏覽器的 `window` 物件，主要用於將當前...
Meta Keywords: scrollby, javascript, window, 一個數值, 100
-->

# scrollBy：JavaScript 中的滾動方法

## 摘要
`scrollBy` 是一個用於在網頁中滾動視窗的 JavaScript 方法，允許開發者根據指定的水平和垂直偏移量來控制內容的滾動。

## 文件說明
`scrollBy` 方法屬於瀏覽器的 `window` 物件，主要用於將當前視窗的滾動位置相對於當前位置進行偏移。這個方法是實現用戶界面互動和動態效果的重要工具，常見於創建無限滾動、模擬滾動等功能。

### 語法
```javascript
window.scrollBy(x, y);
```

### 參數
- `x`：一個數值，表示在水平方向上滾動的像素數量（正值向右滾動，負值向左滾動）。
- `y`：一個數值，表示在垂直方向上滾動的像素數量（正值向下滾動，負值向上滾動）。

### 返回值
此方法不返回任何值（`undefined`）。

## 使用範例
### 基本範例
```javascript
// 向下滾動 100 像素
window.scrollBy(0, 100);
```

### 向右滾動
```javascript
// 向右滾動 50 像素
window.scrollBy(50, 0);
```

### 向左滾動
```javascript
// 向左滾動 30 像素
window.scrollBy(-30, 0);
```

### 向上滾動
```javascript
// 向上滾動 200 像素
window.scrollBy(0, -200);
```

## 解釋
使用 `scrollBy` 時需要注意以下幾點：

1. **相對滾動**：`scrollBy` 是相對於當前滾動位置進行滾動的，不會影響到其他滾動位置或歷史紀錄。
  
2. **性能考量**：過於頻繁地調用 `scrollBy` 可能會影響性能，尤其是在動畫或高頻率的事件中，建議使用 `requestAnimationFrame` 來優化性能。

3. **滾動容器**：`scrollBy` 主要作用於 `window` 物件，若要在特定的滾動容器中使用，需使用該容器的滾動方法，如 `element.scrollBy()`。

4. **滾動行為**：可以搭配 CSS 的 `scroll-behavior` 屬性使用，以平滑的方式進行滾動。

## 總結
`scrollBy` 是一個便捷的 JavaScript 方法，用於在網頁中實現相對滾動效果，能有效提升用戶體驗。