<!--
Meta Description: # HTMLCanvasElement：JavaScript 中的畫布元素 ## 簡介 HTMLCanvasElement 係一個用於在網頁上繪製圖形嘅 JavaScript 物件。佢提供咗一個可編程嘅畫布，讓開發者可以使用 JavaScript 繪製圖像、動畫和其他視覺效果。 ## 文檔 ### ...
Meta Keywords: context, javascript, canvas, const, htmlcanvaselement
-->

# HTMLCanvasElement：JavaScript 中的畫布元素

## 簡介
HTMLCanvasElement 係一個用於在網頁上繪製圖形嘅 JavaScript 物件。佢提供咗一個可編程嘅畫布，讓開發者可以使用 JavaScript 繪製圖像、動畫和其他視覺效果。

## 文檔
### 目的
HTMLCanvasElement 主要用於在 HTML 文件中創建一個可操作的畫布，開發者可以通過 JavaScript 對畫布進行繪製和操作。佢支持 2D 和 3D 渲染，適合用於遊戲開發、數據可視化和其他圖形應用。

### 使用方法
要使用 HTMLCanvasElement，首先需要在 HTML 中創建一個 `<canvas>` 標籤，然後使用 JavaScript 獲取該元素並進行操作。

#### 基本語法
```html
<canvas id="myCanvas" width="500" height="500"></canvas>
```

```javascript
const canvas = document.getElementById('myCanvas');
const context = canvas.getContext('2d'); // 獲取 2D 上下文
```

### 詳細說明
- **屬性**：
  - `width`：畫布的寬度（以像素為單位）。
  - `height`：畫布的高度（以像素為單位）。
  
- **方法**：
  - `getContext(type)`：返回指定類型的繪圖上下文，通常是 `'2d'` 或 `'webgl'`。
  - `toDataURL()`：返回畫布上圖像的數據 URL。

## 範例
### 繪製基本矩形
```javascript
const canvas = document.getElementById('myCanvas');
const context = canvas.getContext('2d');

// 填充矩形
context.fillStyle = 'blue';
context.fillRect(20, 20, 150, 100);
```

### 繪製圓形
```javascript
const canvas = document.getElementById('myCanvas');
const context = canvas.getContext('2d');

// 繪製圓形
context.beginPath();
context.arc(240, 240, 50, 0, Math.PI * 2);
context.fillStyle = 'red';
context.fill();
context.stroke();
```

## 解釋
- **常見問題**：
  - 確保在 DOM 加載完成後再獲取畫布元素，以避免 `null` 錯誤。
  - 當畫布的大小改變時，可能需要重新繪製內容，因為畫布內容不會自動縮放。

- **注意**：
  - 使用 `getContext('webgl')` 時，需要考慮到不同的瀏覽器兼容性。
  - 注意畫布的清空操作，使用 `clearRect()` 方法來清除特定區域。

## 一句總結
HTMLCanvasElement 係 JavaScript 中用於創建和操作可編程畫布的強大工具，適合各種視覺效果和圖形應用。