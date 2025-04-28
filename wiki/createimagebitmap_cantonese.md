<!--
Meta Description: # createImageBitmap：JavaScript 中的圖像位圖創建方法 ## 概述 `createImageBitmap` 是一個用於在 JavaScript 中創建圖像位圖（Bitmap）對象的函數，這對於高效的圖像處理和顯示非常有用。它可以從多種圖像來源創建位圖，例如 `<canva...
Meta Keywords: canvas, createimagebitmap, javascript, bitmap, const
-->

# createImageBitmap：JavaScript 中的圖像位圖創建方法

## 概述
`createImageBitmap` 是一個用於在 JavaScript 中創建圖像位圖（Bitmap）對象的函數，這對於高效的圖像處理和顯示非常有用。它可以從多種圖像來源創建位圖，例如 `<canvas>`、`<img>`、`<video>` 等。

## 文檔
### 目的
`createImageBitmap` 主要用於生成可在 Canvas 上渲染的位圖圖像。它的使用能夠提高圖像加載和渲染的性能，特別是在需要處理大量圖像的應用中。

### 使用方法
`createImageBitmap` 的基本語法如下：

```javascript
createImageBitmap(imageSource, sx, sy, sw, sh, options);
```

#### 參數
- **imageSource**：必需，能夠是 `<img>`、`<canvas>`、`<video>` 或其他可用於生成位圖的圖像來源。
- **sx**：可選，指定用於創建位圖的圖像來源的起始 x 坐標。
- **sy**：可選，指定用於創建位圖的圖像來源的起始 y 坐標。
- **sw**：可選，指定從圖像來源提取的寬度。
- **sh**：可選，指定從圖像來源提取的高度。
- **options**：可選，一個配置對象，可能包括：
  - `imageOrientation`：指定圖像的方向。
  - `premultiplyAlpha`：指定是否預乘 alpha 通道。

### 返回值
此方法返回一個 Promise，解析為創建的 ImageBitmap 對象。

## 範例
### 基本用法示例

1. 從 `<img>` 元素創建位圖：
```javascript
const img = document.getElementById('myImage');
createImageBitmap(img).then(bitmap => {
    // 使用 bitmap，例如在 canvas 上繪製
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');
    ctx.drawImage(bitmap, 0, 0);
});
```

2. 從 `<canvas>` 元素創建位圖：
```javascript
const canvas = document.getElementById('myCanvas');
createImageBitmap(canvas).then(bitmap => {
    // 在另一個 canvas 上使用
    const anotherCanvas = document.getElementById('anotherCanvas');
    const ctx = anotherCanvas.getContext('2d');
    ctx.drawImage(bitmap, 0, 0);
});
```

## 解釋
在使用 `createImageBitmap` 時，開發者需要注意以下幾點：
- 當使用多個圖像來源時，確保這些圖像已經加載完成，否則會導致錯誤。
- 如果指定了 sx、sy、sw、sh，這些參數需要在圖像來源的範圍內，否則會引發異常。
- 生成的 ImageBitmap 是異步的，因此需要使用 Promise 管理異步行為。

## 總結
`createImageBitmap` 是一個高效的圖像處理工具，能夠幫助開發者在 JavaScript 中快速創建可用於渲染的位圖圖像。