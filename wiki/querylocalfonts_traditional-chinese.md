<!--
Meta Description: # queryLocalFonts：JavaScript 中的本地字型查詢功能 ## 概述 `queryLocalFonts` 是一個 JavaScript API，用於查詢用戶系統中的本地字型。這項功能使開發者能夠獲取用戶已安裝字型的列表，進而增強網頁的字型管理和顯示效果。 ## 文檔 ### 目...
Meta Keywords: querylocalfonts, error, fonts, font, console
-->

# queryLocalFonts：JavaScript 中的本地字型查詢功能

## 概述
`queryLocalFonts` 是一個 JavaScript API，用於查詢用戶系統中的本地字型。這項功能使開發者能夠獲取用戶已安裝字型的列表，進而增強網頁的字型管理和顯示效果。

## 文檔
### 目的
`queryLocalFonts` 主要用於獲取用戶本地安裝的字型，這對於設計字型適配的網頁或應用程式至關重要。它可以幫助開發者確保所使用的字型在用戶的設備上可用，從而提升用戶體驗。

### 使用方法
`queryLocalFonts` 方法返回一個包含本地字型資訊的 Promise，該資訊通常包括字型的名稱、樣式及其其他屬性。這個方法的基本語法如下：

```javascript
queryLocalFonts()
    .then(fonts => {
        // 處理字型資訊
        console.log(fonts);
    })
    .catch(error => {
        console.error("無法獲取本地字型: ", error);
    });
```

### 詳細說明
- **返回值**：`queryLocalFonts` 返回一個 Promise，解析後會得到一個字型物件的陣列，每個字型物件包含字型名稱、樣式等屬性。
- **相容性**：目前此功能的支援程度依賴於不同的瀏覽器版本，開發者應該檢查當前瀏覽器的相容性。
- **使用場景**：適用於需要根據用戶環境動態調整字型的網頁設計或應用程式。

## 範例
### 基本用法
以下是一個基本的使用範例，展示如何查詢本地字型並列印出字型名稱：

```javascript
queryLocalFonts()
    .then(fonts => {
        fonts.forEach(font => {
            console.log(`字型名稱: ${font.family}, 樣式: ${font.style}`);
        });
    })
    .catch(error => {
        console.error("錯誤: ", error);
    });
```

### 顯示字型列表
在網頁上顯示用戶本地字型的簡單範例：

```html
<ul id="fontList"></ul>
<script>
    queryLocalFonts()
        .then(fonts => {
            const fontList = document.getElementById('fontList');
            fonts.forEach(font => {
                const listItem = document.createElement('li');
                listItem.textContent = `${font.family} - ${font.style}`;
                fontList.appendChild(listItem);
            });
        })
        .catch(error => {
            console.error("無法獲取字型: ", error);
        });
</script>
```

## 說明
- **常見問題**：某些舊版本的瀏覽器可能不支援 `queryLocalFonts`，開發者需要考慮使用回退方案。
- **性能考量**：查詢本地字型可能會有性能影響，尤其是在字型數量較多的情況下，建議在非阻塞的情況下執行查詢操作。
- **隱私考量**：用戶的字型資訊可能涉及隱私問題，開發者應謹慎處理這些數據。

## 總結
`queryLocalFonts` 是一個強大的工具，幫助開發者查詢用戶本地字型，從而改善網頁的字型管理和用戶體驗。