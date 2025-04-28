<!--
Meta Description: # createImageBitmap：JavaScript 中的圖像處理函數 ## 簡介 `createImageBitmap` 是一個 JavaScript 函數，允許開發者將圖片數據轉換為可用於畫布或其他圖像元素的位圖對象，從而提高圖像處理的效率和性能。 ## 文檔 ### 目的 `creat...
Meta Keywords: canvas, createimagebitmap, blob, bitmap, javascript
-->

# createImageBitmap：JavaScript 中的圖像處理函數

## 簡介
`createImageBitmap` 是一個 JavaScript 函數，允許開發者將圖片數據轉換為可用於畫布或其他圖像元素的位圖對象，從而提高圖像處理的效率和性能。

## 文檔
### 目的
`createImageBitmap` 的主要目的是提供一種簡單而高效的方法來創建位圖，這在進行圖像處理時非常有效，例如在 HTML5 Canvas 中繪製圖像。

### 使用方法
該函數的語法如下：

```javascript
createImageBitmap(imageSource, sx, sy, sw, sh, options);
```

#### 參數
- **imageSource**：可以是 `HTMLImageElement`、`HTMLCanvasElement`、`ImageBitmap`、`ImageData` 或 `Blob` 對象。
- **sx** (可選)：源圖像的 x 坐標，默認為 0。
- **sy** (可選)：源圖像的 y 坐標，默認為 0。
- **sw** (可選)：源圖像的寬度，默認為整個圖像的寬度。
- **sh** (可選)：源圖像的高度，默認為整個圖像的高度。
- **options** (可選)：包含位圖選項的對象，例如 `imageOrientation` 和 `premultiplyAlpha`。

### 返回值
返回一個 `Promise`，解析為 `ImageBitmap` 對象。

### 注意事項
- 當 `imageSource` 是 `Blob` 或 `ImageData` 時，函數將異步處理並返回一個 `Promise`。
- 在使用 `createImageBitmap` 時，確保圖像資源已完全加載。

## 示例
### 基本用法
以下是 `createImageBitmap` 的基本使用示例：

```javascript
const img = new Image();
img.src = 'path/to/image.jpg';
img.onload = () => {
    createImageBitmap(img).then(bitmap => {
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = bitmap.width;
        canvas.height = bitmap.height;
        ctx.drawImage(bitmap, 0, 0);
        document.body.appendChild(canvas);
    });
};
```

### 使用 Blob
你也可以使用 Blob 來創建位圖：

```javascript
fetch('path/to/image.jpg')
    .then(response => response.blob())
    .then(blob => createImageBitmap(blob))
    .then(bitmap => {
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = bitmap.width;
        canvas.height = bitmap.height;
        ctx.drawImage(bitmap, 0, 0);
        document.body.appendChild(canvas);
    });
```

## 解釋
在使用 `createImageBitmap` 時，有幾個常見的陷阱需要注意：
- 確保圖像資源在調用該函數之前已經加載，否則會導致 `Promise` 失敗。
- 使用 Blob 時，請注意 CORS 問題，確保圖像來源支持跨域請求。
- 當處理大圖像時，確保你有足夠的內存來避免性能下降。

## 總結
`createImageBitmap` 是一個高效的 JavaScript 函數，用於創建位圖，提升圖像處理性能，特別適合用於 HTML5 Canvas 的應用場景。