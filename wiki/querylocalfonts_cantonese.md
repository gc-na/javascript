<!--
Meta Description: # 在JavaScript中使用queryLocalFonts命令的完整指南 ## 簡介 `queryLocalFonts` 是一個 JavaScript API，允許開發者查詢用戶系統中安裝的字體。這個功能對於需要自定義字體或進行字體管理的Web應用程式尤為重要。 ## 文檔 ### 目的 `qu...
Meta Keywords: querylocalfonts, javascript, fonts, loadfonts, error
-->

# 在JavaScript中使用queryLocalFonts命令的完整指南

## 簡介
`queryLocalFonts` 是一個 JavaScript API，允許開發者查詢用戶系統中安裝的字體。這個功能對於需要自定義字體或進行字體管理的Web應用程式尤為重要。

## 文檔
### 目的
`queryLocalFonts` 主要用於獲取用戶設備中可用的字體列表，幫助開發者更好地設計和呈現網頁內容，提升用戶體驗。

### 使用方法
`queryLocalFonts` 函數的基本語法如下：

```javascript
const fonts = await queryLocalFonts();
```

這個函數返回一個 Promise，解析為一個包含字體信息的數組。每個字體信息對象包含如下屬性：

- `family`: 字體的家族名稱。
- `style`: 字體的樣式（如正常、斜體）。
- `weight`: 字體的粗細（如常規、加粗）。
- `stretch`: 字體的拉伸程度。

### 詳細信息
`queryLocalFonts` 主要用於字體的動態加載和使用，特別是在需要自定義字體的情況下。這個功能使得開發者可以根據用戶的環境選擇合適的字體，從而提升網站的可讀性和美觀度。

## 範例
以下是 `queryLocalFonts` 的基本使用範例：

```javascript
async function loadFonts() {
    try {
        const fonts = await queryLocalFonts();
        console.log(fonts);
    } catch (error) {
        console.error("無法獲取本地字體:", error);
    }
}

loadFonts();
```

在這個範例中，我們定義了一個異步函數 `loadFonts`，用來查詢本地字體並將其輸出到控制台。

## 說明
- **常見問題**: 在某些瀏覽器中，`queryLocalFonts` 可能不被支持，因此在使用之前最好檢查其兼容性。
- **注意事項**: 確保在調用 `queryLocalFonts` 時，執行上下文已經準備好（如在DOM完全加載後）。

## 一句總結
`queryLocalFonts` 是一個強大的JavaScript API，用於查詢用戶系統中的可用字體，從而提升網頁的設計和可用性。