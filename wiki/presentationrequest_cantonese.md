<!--
Meta Description: # PresentationRequest：JavaScript 的投影請求功能 ## 概述 `PresentationRequest` 是一個用於在 HTML5 瀏覽器中管理投影會議的 JavaScript 介面。它使得網頁應用程式能夠請求將內容投影到外部顯示設備，例如智能電視或投影儀。 ## 文...
Meta Keywords: presentationrequest, javascript, start, presentation, https
-->

# PresentationRequest：JavaScript 的投影請求功能

## 概述
`PresentationRequest` 是一個用於在 HTML5 瀏覽器中管理投影會議的 JavaScript 介面。它使得網頁應用程式能夠請求將內容投影到外部顯示設備，例如智能電視或投影儀。

## 文檔
### 目的
`PresentationRequest` 旨在簡化網頁應用程式與外部顯示設備之間的互動，提供一種標準化的方式來發送媒體和內容。

### 使用方式
要使用 `PresentationRequest`，開發者需要創建一個新的 `PresentationRequest` 實例，並指定要投影的媒體 URL。然後，可以調用 `start()` 方法開始投影請求。

### 詳細信息
- **建構函數**：`new PresentationRequest(urls)`
  - `urls`：一個包含要顯示的媒體 URL 的陣列。
  
- **方法**：
  - `start()`：啟動投影請求，並返回一個 `Promise`，該 Promise 解析為一個 `Presentation` 實例。
  - `getAvailability()`：檢查設備是否可用以進行投影。

- **事件**：
  - `onconnectionavailable`：當有可用的投影設備時觸發。
  - `onconnectionlost`：當投影設備失去連接時觸發。

## 範例
以下是使用 `PresentationRequest` 的基本範例：

```javascript
// 創建投影請求
const request = new PresentationRequest(['https://example.com/media.mp4']);

// 開始投影請求
request.start().then(presentation => {
    console.log('投影已開始:', presentation);
}).catch(error => {
    console.error('投影請求失敗:', error);
});
```

## 解釋
使用 `PresentationRequest` 時，有一些常見的陷阱和注意事項：

- **支持性**：並非所有瀏覽器都支持 `PresentationRequest`。開發者應檢查用戶的瀏覽器兼容性。
- **HTTPS**：投影請求需要在安全上下文中運行，通常要求使用 HTTPS 協議。
- **用戶互動**：大多數瀏覽器對於投影請求有用戶互動的要求，即必須由用戶的操作來觸發請求。

## 簡要總結
`PresentationRequest` 是一個強大的 JavaScript 介面，用於管理網頁應用程式的投影請求，簡化與外部顯示設備的互動。