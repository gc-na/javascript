<!--
Meta Description: # FontFace：JavaScript 字型管理工具 ## 概述 `FontFace` 是一個用於在網頁中動態管理字型的 JavaScript API。它允許開發者直接在 JavaScript 中創建和加載字型，從而提升網頁的字型控制能力和靈活性。 ## 文檔 ### 目的 `FontFace`...
Meta Keywords: fontface, javascript, document, error, url
-->

# FontFace：JavaScript 字型管理工具

## 概述
`FontFace` 是一個用於在網頁中動態管理字型的 JavaScript API。它允許開發者直接在 JavaScript 中創建和加載字型，從而提升網頁的字型控制能力和靈活性。

## 文檔
### 目的
`FontFace` 的主要目的是提供一種方式來動態加載和使用自訂字型，這樣開發者可以不依賴於 CSS 文件來引入字型，進而提高網頁的性能和使用者體驗。

### 使用方法
`FontFace` 的基本語法如下：

```javascript
let myFont = new FontFace('FontName', 'url(/path/to/font.woff2)');
```

- **FontName**：字型的名稱，這將在 CSS 中用於引用此字型。
- **url**：字型文件的路徑，可以是相對路徑或絕對路徑。

#### 加載字型
要使字型在網頁中可用，必須調用 `load` 方法：

```javascript
myFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = 'FontName';
}).catch(function(error) {
    console.error('字型加載失敗：', error);
});
```

### 詳細信息
- `FontFace` 物件還可以接收其他參數，例如 `descriptors`，這些參數可用於定義字型樣式、粗細、斜體等屬性。
- `document.fonts` 提供了一個字型集合，允許開發者檢索和管理已加載的字型。
 
## 範例
以下是一個簡單的例子，示範如何使用 `FontFace` 加載並應用自訂字型：

```javascript
let customFont = new FontFace('MyCustomFont', 'url(myCustomFont.woff2)');

customFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = 'MyCustomFont, sans-serif';
}).catch(function(error) {
    console.error('字型加載失敗：', error);
});
```

## 解釋
### 常見問題
1. **字型無法加載**：確保字型文件的 URL 正確，並檢查網絡請求是否成功。
2. **字型未應用**：在將字型添加到 `document.fonts` 之前，必須確保 `load` 方法已成功完成。
3. **跨域問題**：如果字型文件位於不同的域，請確保伺服器設置了正確的 CORS 標頭。

### 附註
- `FontFace` API 目前在大多數現代瀏覽器中均受支持，但在某些舊版瀏覽器中可能不兼容。
- 使用 `FontFace` 可以提高頁面加載速度，因為它允許在 JavaScript 中控制字型的加載時機。

## 一行總結
`FontFace` 是一個強大的 JavaScript API，允許開發者在網頁中動態加載和使用自訂字型。