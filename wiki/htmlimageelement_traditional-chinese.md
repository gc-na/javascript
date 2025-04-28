<!--
Meta Description: # HTMLImageElement：JavaScript 中的圖片元素 ## 摘要 `HTMLImageElement` 是一個用於操作和控制 HTML 中 `<img>` 標籤的 JavaScript 物件，提供了豐富的方法和屬性來處理圖片的顯示和行為。 ## 文檔 `HTMLImageElem...
Meta Keywords: htmlimageelement, document, javascript, img, imgelement
-->

# HTMLImageElement：JavaScript 中的圖片元素

## 摘要
`HTMLImageElement` 是一個用於操作和控制 HTML 中 `<img>` 標籤的 JavaScript 物件，提供了豐富的方法和屬性來處理圖片的顯示和行為。

## 文檔
`HTMLImageElement` 是 Document Object Model (DOM) 中的一個接口，專門用於表示 HTML `<img>` 標籤。這個接口允許開發者以編程方式訪問和修改圖片的屬性，例如源 URL、寬度、高度等。

### 目的
`HTMLImageElement` 主要用於：
- 控制圖片的顯示屬性
- 動態加載和更新圖片
- 獲取圖片的加載狀態和尺寸

### 使用方法
要操作 `HTMLImageElement`，首先需要獲取對應的 `<img>` 元素，可以使用 `document.getElementById` 或 `document.querySelector` 方法：

```javascript
const imgElement = document.getElementById('myImage'); // 獲取圖片元素
```

### 詳細屬性與方法
- **src**: 圖片的來源 URL。
- **alt**: 圖片的替代文本，當圖片無法顯示時用於顯示描述。
- **width**: 圖片的顯示寬度（以像素為單位）。
- **height**: 圖片的顯示高度（以像素為單位）。
- **naturalWidth**: 圖片的原始寬度（以像素為單位）。
- **naturalHeight**: 圖片的原始高度（以像素為單位）。
- **complete**: 一個布林值，用於檢查圖片是否已經完全加載。
- **onload**: 當圖片成功加載時執行的事件處理器。
- **onerror**: 當圖片加載失敗時執行的事件處理器。

## 範例
### 基本使用範例
```html
<img id="myImage" src="image.jpg" alt="描述文本" />

<script>
  const imgElement = document.getElementById('myImage');
  imgElement.onload = function() {
    console.log('圖片已加載');
  };
  imgElement.onerror = function() {
    console.log('圖片加載失敗');
  };
  
  // 更新圖片源
  imgElement.src = 'newImage.jpg';
</script>
```

### 動態創建圖片元素
```javascript
const newImage = new Image();
newImage.src = 'dynamicImage.jpg';
newImage.alt = '動態創建的圖片';
document.body.appendChild(newImage);
```

## 說明
在使用 `HTMLImageElement` 時，有幾個常見的注意事項：
- 確保圖片的 URL 正確，否則會觸發 `onerror` 事件。
- 使用 `onload` 事件來確認圖片是否成功加載，避免在圖片未加載完成時操作其屬性。
- 當修改 `src` 屬性時，舊的圖片會被釋放，並開始加載新的圖片。

## 一句總結
`HTMLImageElement` 是 JavaScript 中用於操作和控制 HTML `<img>` 標籤的接口，提供了多種屬性和方法來處理圖片的顯示和行為。