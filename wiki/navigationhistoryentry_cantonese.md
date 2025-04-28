<!--
Meta Description: # NavigationHistoryEntry：JavaScript 中的導航歷史條目 ## 簡介 `NavigationHistoryEntry` 是一個在 JavaScript 瀏覽器環境中使用的接口，用於表示瀏覽器的導航歷史條目，包含用戶在網頁上訪問的資訊。 ## 文檔 `Navigatio...
Meta Keywords: navigationhistoryentry, url, javascript, title, currententry
-->

# NavigationHistoryEntry：JavaScript 中的導航歷史條目

## 簡介
`NavigationHistoryEntry` 是一個在 JavaScript 瀏覽器環境中使用的接口，用於表示瀏覽器的導航歷史條目，包含用戶在網頁上訪問的資訊。

## 文檔
`NavigationHistoryEntry` 介面提供了一種方法來訪問和操作用戶的瀏覽歷史。每個條目都包含有關當前網頁的各種資訊，像是網址、標題和狀態等。這有助於開發者在處理網頁導航時管理用戶的歷史記錄。

### 目的
- 提供訪問用戶瀏覽歷史的能力。
- 允許開發者獲取當前條目的詳細資訊。

### 用法
`NavigationHistoryEntry` 目前主要用於 Web API 中，幫助開發者在應用程序中進行導航管理。

### 詳細信息
- **屬性**：
  - `url`：當前條目的 URL。
  - `title`：當前條目的標題。
  - `state`：與當前條目相關的狀態對象。

### 方法
- `getEntries()`：獲取導航歷史的所有條目。

## 範例

### 基本用法
```javascript
// 獲取當前導航條目的 URL
const currentEntry = window.history.state;
console.log(currentEntry.url);

// 獲取當前導航條目的標題
console.log(currentEntry.title);
```

### 獲取歷史條目
```javascript
const historyEntries = window.history.entries;

for (let entry of historyEntries) {
    console.log(`URL: ${entry.url}, Title: ${entry.title}`);
}
```

## 解釋
在使用 `NavigationHistoryEntry` 時，開發者應注意以下幾點：
- 瀏覽器兼容性：並非所有瀏覽器都支持所有功能，開發者應檢查支持情況。
- 事件觸發：當用戶在導航歷史中移動時，可能需要處理相應事件來更新應用狀態。

## 一句總結
`NavigationHistoryEntry` 使開發者能輕鬆訪問和管理用戶的瀏覽歷史條目。