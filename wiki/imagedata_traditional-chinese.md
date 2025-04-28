<!--
Meta Description: # ImageData 在 JavaScript 中的應用與使用 ## 概述 `ImageData` 是一個 JavaScript 物件，專門用於處理圖像數據。它提供了一種高效的方式來反映和操作畫布上的像素，特別在 Web 圖形編程中扮演著重要角色。 ## 文檔 ### 目的 `ImageData`...
Meta Keywords: imagedata, data, javascript, width, height
-->

# ImageData 在 JavaScript 中的應用與使用

## 概述
`ImageData` 是一個 JavaScript 物件，專門用於處理圖像數據。它提供了一種高效的方式來反映和操作畫布上的像素，特別在 Web 圖形編程中扮演著重要角色。

## 文檔
### 目的
`ImageData` 物件用於表示圖像數據，包含圖像的寬度、高度以及每個像素的 RGBA 值。這對於需要直接操作圖像像素的應用（如圖像處理、視覺效果等）非常有用。

### 使用方式
`ImageData` 可以通過 `CanvasRenderingContext2D.createImageData()` 方法創建，或使用 `CanvasRenderingContext2D.getImageData()` 方法從畫布中獲取。其基本結構如下：

```javascript
let imageData = new ImageData(width, height);
```

### 詳細說明
- **屬性**：
  - `width`：代表圖像的寬度（以像素為單位）。
  - `height`：代表圖像的高度（以像素為單位）。
  - `data`：一個 `Uint8ClampedArray`，包含圖像的 RGBA 像素數據，每四個數字代表一個像素的紅、綠、藍和透明度（Alpha）值。

- **方法**：
  - `createImageData(width, height)`：創建一個新的 `ImageData` 物件。
  - `getImageData(sx, sy, sw, sh)`：從指定的畫布區域獲取 `ImageData`。

## 範例
### 基本使用範例
以下是一個基本範例，展示如何在畫布上創建和操作 `ImageData`：

```javascript
// 獲取畫布上下文
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// 創建 ImageData 物件
const imageData = ctx.createImageData(100, 100);

// 填充圖像數據
for (let i = 0; i < imageData.data.length; i += 4) {
  imageData.data[i] = 255; // Red
  imageData.data[i + 1] = 0; // Green
  imageData.data[i + 2] = 0; // Blue
  imageData.data[i + 3] = 255; // Alpha
}

// 將 ImageData 放入畫布中
ctx.putImageData(imageData, 0, 0);
```

### 從畫布獲取 ImageData
```javascript
// 獲取畫布的圖像數據
const data = ctx.getImageData(0, 0, canvas.width, canvas.height);
console.log(data);
```

## 解釋
使用 `ImageData` 時需注意以下幾點：
- `ImageData` 的 `data` 陣列使用 RGBA 格式，必須以 0 到 255 的值表示顏色和透明度。
- 在處理大量像素時，執行性能可能受限，因此建議使用 Web Workers 進行計算密集型任務。
- `ImageData` 不支持直接以圖像的文件格式（如 JPEG 或 PNG）來表示圖像，需先將圖像繪製至畫布中。

## 單行摘要
`ImageData` 是一個用於處理和操作畫布上像素數據的 JavaScript 物件，對於圖像編輯和視覺效果創建至關重要。