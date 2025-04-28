<!--
Meta Description: # FontFace：使用 JavaScript 動態加載字型 ## 摘要 FontFace 是一個 JavaScript API，允許開發者動態加載自定義字型，以便在網頁中使用，從而增強網站的外觀和可讀性。 ## 文檔 FontFace 接口提供了一種方法來創建和加載新的字型。這個 API 允許開...
Meta Keywords: fontface, api, myfont, javascript, url
-->

# FontFace：使用 JavaScript 動態加載字型

## 摘要
FontFace 是一個 JavaScript API，允許開發者動態加載自定義字型，以便在網頁中使用，從而增強網站的外觀和可讀性。

## 文檔
FontFace 接口提供了一種方法來創建和加載新的字型。這個 API 允許開發者將字型文件與 CSS 結合使用，從而在不同的瀏覽器中一致地顯示字型。開發者可以指定字型的名稱、來源和其他屬性。使用 FontFace 的主要目的在於提高字型渲染的靈活性和控制。

### 主要屬性：
- **family**: 字型的名稱。
- **source**: 字型文件的 URL，可以是字符串或 Blob 物件。
- **style**: 字型的樣式（例如 'normal' 或 'italic'）。
- **weight**: 字型的粗細（例如 'normal' 或 'bold'）。
- **stretch**: 字型的拉伸程度（例如 'normal'、'condensed' 或 'expanded'）。

### 方法：
- **load()**: 用於加載字型，返回一個 Promise，表示字型的加載狀態。

## 範例
以下是使用 FontFace API 的基本範例：

```javascript
// 創建一個 FontFace 實例
const myFont = new FontFace('MyFont', 'url(/fonts/myfont.woff2)');

// 加載字型
myFont.load().then(function(loadedFont) {
    // 將字型添加到文檔
    document.fonts.add(loadedFont);
    // 設定字型樣式
    document.body.style.fontFamily = 'MyFont, sans-serif';
}).catch(function(error) {
    console.error('字型加載失敗:', error);
});
```

## 解釋
使用 FontFace API 時，開發者可能會遇到幾個常見的問題：
- **字型加載失敗**: 確保字型 URL 正確且可訪問。如果字型文件不存在或有 CORS 問題，則加載會失敗。
- **字型名稱衝突**: 如果使用相同的字型名稱加載多個字型，可能會導致不一致的渲染結果。
- **性能考量**: 動態加載字型可能會影響頁面加載性能，建議在需要的時候才進行加載。

## 單行摘要
FontFace API 允許開發者動態加載和使用自定義字型，以提升網頁的設計和可讀性。