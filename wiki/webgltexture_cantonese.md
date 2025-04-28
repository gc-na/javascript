<!--
Meta Description: # WebGLTexture 在 JavaScript 中的應用 ## 簡介 WebGLTexture 是 WebGL API 中用於處理和操作紋理的對象。它使開發者能夠在網頁上使用硬體加速的 3D 圖形，並加載和顯示紋理。 ## 文檔 ### 目的 WebGLTexture 對象的主要用途是將紋理...
Meta Keywords: image, texture_2d, javascript, const, webgl
-->

# WebGLTexture 在 JavaScript 中的應用

## 簡介
WebGLTexture 是 WebGL API 中用於處理和操作紋理的對象。它使開發者能夠在網頁上使用硬體加速的 3D 圖形，並加載和顯示紋理。

## 文檔
### 目的
WebGLTexture 對象的主要用途是將紋理映射到 3D 物件上。這些紋理可以是圖像、顏色漸變或其他圖形資料，旨在增強視覺效果和用戶體驗。

### 使用方法
在使用 WebGLTexture 之前，您需要先創建一個 WebGL 上下文，然後利用該上下文來創建和管理紋理。以下是基本的使用步驟：

1. **創建 WebGL 上下文**：
   ```javascript
   const canvas = document.createElement('canvas');
   const gl = canvas.getContext('webgl');
   ```

2. **創建紋理**：
   ```javascript
   const texture = gl.createTexture();
   ```

3. **綁定紋理**：
   ```javascript
   gl.bindTexture(gl.TEXTURE_2D, texture);
   ```

4. **設置紋理參數**：
   ```javascript
   gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_S, gl.CLAMP_TO_EDGE);
   gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_T, gl.CLAMP_TO_EDGE);
   gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MIN_FILTER, gl.LINEAR);
   ```

5. **上傳紋理數據**：
   ```javascript
   const image = new Image();
   image.src = 'path/to/your/image.png';
   image.onload = () => {
       gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, gl.UNSIGNED_BYTE, image);
   };
   ```

6. **釋放紋理**：
   ```javascript
   gl.deleteTexture(texture);
   ```

## 範例
以下是一個簡單的範例，展示如何在畫布上加載和顯示一個圖像紋理：

```javascript
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl');

const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

const image = new Image();
image.src = 'path/to/your/image.jpg';
image.onload = () => {
   gl.bindTexture(gl.TEXTURE_2D, texture);
   gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, gl.UNSIGNED_BYTE, image);
   gl.generateMipmap(gl.TEXTURE_2D);
};
```

## 解釋
- **常見問題**：
   - 確保圖像在加載完成後再上傳至紋理，否則可能會導致錯誤。
   - 如果紋理顯示不正常，檢查紋理參數設置，例如過濾器和包裝模式。

- **注意事項**：
   - 使用 `gl.generateMipmap` 可以自動生成各種大小的紋理，這樣在縮放時可以保持質量。
   - 確保釋放不再需要的紋理以釋放內存。

## 總結
WebGLTexture 是 WebGL 中用於高效管理和應用紋理的關鍵對象，使得在網頁中構建 3D 圖形變得更加簡便和強大。