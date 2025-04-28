<!--
Meta Description: # JavaScript 圖像處理：全面指南 ## 簡介 在 JavaScript 中，圖像處理是網頁開發中不可或缺的一部分。通過使用 JavaScript，開發者能夠動態加載、顯示和操作圖像，以提升用戶體驗與網站互動性。 ## 文檔 ### 目的 JavaScript 提供多種方法來處理圖像，例如...
Meta Keywords: img, canvas, javascript, const, src
-->

# JavaScript 圖像處理：全面指南

## 簡介
在 JavaScript 中，圖像處理是網頁開發中不可或缺的一部分。通過使用 JavaScript，開發者能夠動態加載、顯示和操作圖像，以提升用戶體驗與網站互動性。

## 文檔
### 目的
JavaScript 提供多種方法來處理圖像，例如使用 `<img>` 標籤、Canvas API、以及其他庫（如 Fabric.js 和 PixiJS）來進行圖像的加載、顯示和處理。

### 用法
1. **使用 `<img>` 標籤顯示圖像**
   ```html
   <img src="image.jpg" alt="描述文字" id="myImage">
   ```
   這段代碼將靜態圖像顯示在網頁上。

2. **動態加載圖像**
   ```javascript
   const img = new Image();
   img.src = 'image.jpg';
   img.onload = function() {
       document.body.appendChild(img);
   };
   ```
   當圖像加載完成後，將其添加到文檔中。

3. **Canvas API 操作圖像**
   ```html
   <canvas id="myCanvas" width="500" height="500"></canvas>
   ```
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   const img = new Image();
   img.src = 'image.jpg';
   img.onload = function() {
       ctx.drawImage(img, 0, 0);
   };
   ```
   使用 Canvas API 可實現圖像的繪製和處理。

### 詳細說明
- **圖像格式**：支持多種格式，如 JPEG、PNG、GIF 等。
- **加載事件**：使用 `onload` 事件確保圖像在使用前已經完全加載。
- **錯誤處理**：利用 `onerror` 事件來處理圖像加載失敗的情況。
- **跨域問題**：使用不同域的圖像時需注意 CORS 問題，以避免安全性限制。

## 範例
### 基本使用範例
1. 靜態圖像顯示
   ```html
   <img src="logo.png" alt="網站標誌">
   ```

2. 動態圖像加載
   ```javascript
   const img = new Image();
   img.src = 'https://example.com/picture.jpg';
   img.onload = () => {
       document.body.appendChild(img);
   };
   img.onerror = () => {
       console.error('圖像加載失敗');
   };
   ```

3. 使用 Canvas 繪製圖像
   ```javascript
   const canvas = document.getElementById('canvas');
   const ctx = canvas.getContext('2d');
   const img = new Image();
   img.src = 'https://example.com/photo.jpg';
   img.onload = () => {
       ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
   };
   ```

## 解釋
- **常見問題**：在使用 `<img>` 標籤時，確保 `src` 屬性指向有效的圖像路徑，否則會導致圖像無法顯示。
- **性能考量**：大量圖像的加載可能會影響頁面性能，建議使用圖像懶加載技術。
- **響應式設計**：確保圖像的大小和比例在不同設備上都能正確顯示。

## 一句總結
在 JavaScript 中，圖像處理是一項關鍵技術，能顯著提升用戶體驗和網頁互動性。