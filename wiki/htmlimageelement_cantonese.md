<!--
Meta Description: # HTMLImageElement：JavaScript 中的圖像元素操作 ## 簡介 `HTMLImageElement` 是 JavaScript 中用來處理 HTML `<img>` 標籤的對象，允許開發者動態操作圖像元素的屬性和行為。 ## 文檔 `HTMLImageElement` 代表...
Meta Keywords: img, javascript, htmlimageelement, console, html
-->

# HTMLImageElement：JavaScript 中的圖像元素操作

## 簡介
`HTMLImageElement` 是 JavaScript 中用來處理 HTML `<img>` 標籤的對象，允許開發者動態操作圖像元素的屬性和行為。

## 文檔
`HTMLImageElement` 代表一個 HTML `<img>` 元素的 JavaScript 對象。這個對象提供了各種屬性和方法來控制圖像的顯示和行為。通過這個對象，開發者可以輕鬆地加載、修改、和處理圖像。

### 主要屬性：
- **src**: 圖像的 URL。
- **alt**: 圖像無法顯示時的替代文本。
- **width**: 圖像的顯示寬度（以像素為單位）。
- **height**: 圖像的顯示高度（以像素為單位）。
- **complete**: 一個布林值，指示圖像是否已經加載完成。

### 主要方法：
- **decode()**: 解碼圖像（異步），在圖像加載完成後執行。
  
### 使用方法：
要使用 `HTMLImageElement`，首先需要在 HTML 文件中創建一個 `<img>` 標籤，然後通過 JavaScript 來引用和操作它。

## 示例
以下是一些基本用法的示例：

### 創建和設置圖像
```javascript
// 創建一個新的圖片元素
const img = new Image();

// 設置圖片的屬性
img.src = 'https://example.com/image.jpg';
img.alt = '這是一張示範圖片';
img.width = 300;
img.height = 200;

// 將圖片添加到文檔中
document.body.appendChild(img);
```

### 檢查圖像是否加載完成
```javascript
img.onload = function() {
    console.log('圖片加載完成！');
};

img.onerror = function() {
    console.log('圖片加載失敗！');
};
```

### 解碼圖像
```javascript
img.decode().then(() => {
    console.log('圖片解碼完成！');
}).catch(err => {
    console.error('解碼失敗：', err);
});
```

## 解釋
在使用 `HTMLImageElement` 時，有一些常見的陷阱需要注意：
- 確保圖像的 URL 正確無誤，否則會導致加載失敗。
- 當圖像未完全加載時，直接訪問它的屬性可能會導致錯誤，建議使用 `onload` 事件來處理加載邏輯。
- 使用 `decode()` 方法時，請注意它是異步的，因此需要適當處理 Promise。

## 總結
`HTMLImageElement` 是 JavaScript 中操作 `<img>` 標籤的強大工具，能夠輕鬆加載和處理圖像。