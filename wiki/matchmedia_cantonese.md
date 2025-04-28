<!--
Meta Description: # matchMedia：JavaScript 中的媒體查詢 API ## 簡介 `matchMedia` 是一個 JavaScript API，允許開發者根據媒體查詢的結果來執行特定的代碼。這個功能對於響應式設計至關重要，幫助開發者根據不同的設備特性（如螢幕大小或方向）來調整應用程序的行為。 ##...
Meta Keywords: matchmedia, mediaquerylist, javascript, api, addlistener
-->

# matchMedia：JavaScript 中的媒體查詢 API

## 簡介
`matchMedia` 是一個 JavaScript API，允許開發者根據媒體查詢的結果來執行特定的代碼。這個功能對於響應式設計至關重要，幫助開發者根據不同的設備特性（如螢幕大小或方向）來調整應用程序的行為。

## 文檔
### 目的
`matchMedia` 的主要目的是提供一種方法來檢查媒體查詢的狀態，並在狀態改變時觸發相應的事件。它可以用來實現更靈活的響應式設計，根據用戶的設備環境做出相應的調整。

### 使用方式
`matchMedia` 函數接受一個媒體查詢字符串作為參數，並返回一個 `MediaQueryList` 對象。這個對象包含了一些屬性和方法，可以用來檢查媒體查詢的狀態，並註冊事件監聽器以監控狀態的變化。

#### 語法
```javascript
const mediaQueryList = window.matchMedia(mediaQueryString);
```

#### 參數
- `mediaQueryString`: 一個字符串，定義了媒體查詢的條件，例如 `"(max-width: 600px)"`。

#### 返回值
`matchMedia` 返回一個 `MediaQueryList` 對象，該對象包含以下關鍵屬性：
- `matches`: 一個布爾值，指示媒體查詢是否匹配。
- `media`: 返回媒體查詢的字符串。
- `addListener(callback)`: 添加一個監聽器，當媒體查詢的狀態改變時會調用該回調函數。
- `removeListener(callback)`: 移除監聽器。

### 例子
#### 基本使用範例
```javascript
// 創建一個媒體查詢列表
const mediaQueryList = window.matchMedia("(max-width: 600px)");

// 定義回調函數
function handleMediaQueryChange(e) {
    if (e.matches) {
        console.log("螢幕寬度小於或等於600px");
    } else {
        console.log("螢幕寬度大於600px");
    }
}

// 添加事件監聽器
mediaQueryList.addListener(handleMediaQueryChange);

// 初始檢查
handleMediaQueryChange(mediaQueryList);
```

### 解釋
- **常見陷阱**：在使用 `addListener` 和 `removeListener` 時，需要確保傳遞的回調函數相同，以便正確移除監聽器。
- **跨瀏覽器兼容性**：雖然大部分現代瀏覽器都支持 `matchMedia`，但需要注意一些舊版本的瀏覽器可能不支持此功能，因此在使用時應考慮到兼容性。
- **性能考量**：過多的媒體查詢監聽器會影響性能，建議根據需要進行優化。

## 一句總結
`matchMedia` 是一個強大的 JavaScript API，用於根據媒體查詢的狀態執行特定代碼，促進響應式設計的實現。