<!--
Meta Description: # JavaScript 中的圖像處理 ## 摘要 在 JavaScript 中，圖像處理是前端開發的重要組成部分。本篇文章將探討如何在網頁中使用圖像，以及相關的 API 和技術，以增強用戶體驗。 ## 文檔 ### 目的 JavaScript 提供多種方法來操縱和顯示圖像，從而使開發者能夠創建豐富...
Meta Keywords: img, canvas, image, javascript, html
-->

# JavaScript 中的圖像處理

## 摘要
在 JavaScript 中，圖像處理是前端開發的重要組成部分。本篇文章將探討如何在網頁中使用圖像，以及相關的 API 和技術，以增強用戶體驗。

## 文檔
### 目的
JavaScript 提供多種方法來操縱和顯示圖像，從而使開發者能夠創建豐富的多媒體網頁。這包括使用 HTML `<img>` 標籤、Canvas API 以及圖像加載和處理的各種技術。

### 用法
1. **使用 `<img>` 標籤**:
   在 HTML 中，使用 `<img>` 標籤可以輕鬆地插入圖像。
   ```html
   <img src="path/to/image.jpg" alt="描述文字" />
   ```

2. **使用 Canvas API**:
   Canvas API 允許你以編程方式繪製和處理圖像。
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   const img = new Image();
   img.src = 'path/to/image.jpg';
   img.onload = function() {
       ctx.drawImage(img, 0, 0);
   };
   ```

3. **圖像加載**:
   使用 JavaScript 可以檢查圖像是否已經加載完畢。
   ```javascript
   const img = new Image();
   img.src = 'path/to/image.jpg';
   img.onload = function() {
       console.log('圖像已加載');
   };
   img.onerror = function() {
       console.log('圖像加載失敗');
   };
   ```

## 示例
### 基本用法
```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>圖像示例</title>
</head>
<body>
    <h1>我的圖像</h1>
    <img src="path/to/image.jpg" alt="示例圖像" />
    <canvas id="myCanvas" width="500" height="500"></canvas>

    <script>
        const canvas = document.getElementById('myCanvas');
        const ctx = canvas.getContext('2d');
        const img = new Image();
        img.src = 'path/to/image.jpg';
        img.onload = function() {
            ctx.drawImage(img, 0, 0);
        };
    </script>
</body>
</html>
```

## 解釋
### 常見問題
- **圖像未顯示**:
  確保圖像的 `src` 路徑正確，並且圖像文件存在。使用開發者工具檢查控制台是否有錯誤信息。

- **Canvas 上的圖像處理**:
  確保在圖像加載完成後再進行繪製，否則可能會出現空白畫布。

- **性能考量**:
  避免在大量圖像上使用 Canvas API，這可能會影響性能。考慮使用圖像精靈或 CSS 背景圖像來優化加載時間。

## 一句總結
JavaScript 提供了強大的工具來處理和顯示圖像，能夠提升網頁的視覺效果和用戶體驗。