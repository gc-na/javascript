<!--
Meta Description: # pageXOffset：JavaScript 中的橫向滾動位置屬性 ## 簡介 `pageXOffset` 是一個在 JavaScript 中用於獲取當前頁面橫向滾動位置的屬性。它返回一個數值，表示頁面已經滾動的像素數量，對於開發者而言，這是一個非常有用的屬性，特別是在處理滾動事件或進行元素定位...
Meta Keywords: pagexoffset, window, javascript, scrollposition, document
-->

# pageXOffset：JavaScript 中的橫向滾動位置屬性

## 簡介
`pageXOffset` 是一個在 JavaScript 中用於獲取當前頁面橫向滾動位置的屬性。它返回一個數值，表示頁面已經滾動的像素數量，對於開發者而言，這是一個非常有用的屬性，特別是在處理滾動事件或進行元素定位時。

## 文檔
### 目的
`pageXOffset` 用於獲取當前文檔在水平方向上的滾動距離。這個屬性是只讀的，通常與 `window` 物件一起使用。

### 使用方法
要使用 `pageXOffset`，只需訪問 `window` 物件的這個屬性。例如：

```javascript
let scrollPosition = window.pageXOffset;
console.log(scrollPosition);
```

這段代碼將輸出當前頁面橫向滾動的像素數量。

### 詳細信息
- **返回值**：`pageXOffset` 返回一個整數，表示頁面橫向滾動的像素數量。
- **支援性**：該屬性在大多數現代瀏覽器中均受支援，包括 Chrome、Firefox、Safari 和 Edge。
- **替代方法**：在某些舊版瀏覽器中，可能需要使用 `document.body.scrollLeft` 或 `document.documentElement.scrollLeft` 來獲取相同的信息。但這不是最佳實踐。

## 示例
以下是幾個基本的使用示例：

### 示例 1：獲取當前橫向滾動位置
```javascript
window.addEventListener('scroll', function() {
    console.log('當前橫向滾動位置：', window.pageXOffset);
});
```

### 示例 2：在滾動時更新位置
```javascript
function updateScrollPosition() {
    let posX = window.pageXOffset;
    document.getElementById('scrollPosition').innerText = `橫向滾動位置：${posX}px`;
}

window.addEventListener('scroll', updateScrollPosition);
```

## 解釋
- **常見誤區**：一些開發者可能會混淆 `pageXOffset` 與 `scrollX`，這兩者功能相似，但 `scrollX` 是 `window` 物件的一個別名，使用時需注意。
- **性能考量**：在高頻率的滾動事件中，頻繁訪問 `pageXOffset` 可能影響性能，建議使用防抖或節流技術來優化性能。
- **文檔兼容性**：雖然 `pageXOffset` 在大多數現代瀏覽器中都能正常工作，但在處理老舊瀏覽器時，仍需考慮相應的替代方案。

## 一句總結
`pageXOffset` 是一個用於獲取當前頁面橫向滾動位置的屬性，在 JavaScript 中非常實用。