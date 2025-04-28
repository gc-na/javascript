<!--
Meta Description: # pageYOffset：JavaScript 的網頁垂直偏移量屬性 ## 概述 `pageYOffset` 是一個用於獲取當前網頁垂直滾動偏移量的全局屬性。在用戶滾動網頁時，該屬性的值會隨之變化，對於需要實現滾動效果或動態更新內容的應用場景非常有用。 ## 文檔 `pageYOffset` 是一...
Meta Keywords: pageyoffset, window, javascript, header, let
-->

# pageYOffset：JavaScript 的網頁垂直偏移量屬性

## 概述
`pageYOffset` 是一個用於獲取當前網頁垂直滾動偏移量的全局屬性。在用戶滾動網頁時，該屬性的值會隨之變化，對於需要實現滾動效果或動態更新內容的應用場景非常有用。

## 文檔
`pageYOffset` 是一個只讀屬性，屬於 `window` 對象。它返回從網頁頂部開始向下滾動的像素數量。這個屬性在滾動事件處理程序中尤其常用，因為它允許開發者根據用戶的滾動位置更新界面。

### 使用方法
```javascript
let scrollPosition = window.pageYOffset;
```

### 目的
`pageYOffset` 主要用於：
- 確定用戶當前的滾動位置。
- 在滾動時觸發特定的事件或效果，例如懸浮效果或動畫。

## 示例
以下是 `pageYOffset` 的基本使用示例：

### 示例 1：獲取當前滾動位置
```javascript
window.addEventListener('scroll', function() {
    console.log('當前滾動位置：', window.pageYOffset);
});
```

### 示例 2：根據滾動位置改變元素樣式
```javascript
window.addEventListener('scroll', function() {
    let header = document.querySelector('header');
    if (window.pageYOffset > 100) {
        header.style.backgroundColor = 'rgba(0, 0, 0, 0.7)';
    } else {
        header.style.backgroundColor = 'transparent';
    }
});
```

## 解釋
在使用 `pageYOffset` 時，有幾個常見的注意事項：
- **兼容性**：`pageYOffset` 在所有現代瀏覽器中均可正常使用，但在某些舊版本的 IE 中可能不支持。確保在需要支持的環境中進行測試。
- **性能**：在滾動事件中頻繁訪問 `pageYOffset` 可能會導致性能問題。考慮使用防抖或節流技術來優化性能。
- **固定元素**：如果使用固定定位的元素，當滾動時，這些元素的樣式可能會受到影響，因為 `pageYOffset` 只考慮了整個文檔的滾動位置。

## 一行總結
`pageYOffset` 是一個用於獲取當前網頁垂直滾動位置的 JavaScript 屬性，對於實現滾動效果和動態更新內容非常有幫助。