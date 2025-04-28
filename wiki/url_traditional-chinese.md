<!--
Meta Description: # JavaScript 中的 URL：完整指南 ## 概述 在 JavaScript 中，URL（統一資源定位符）是用來標識和定位網絡資源的字符串。URL 不僅在網頁中導航至不同的資源，還在 AJAX 請求、API 呼叫等操作中扮演關鍵角色。 ## 文檔 ### 目的 URL 在 JavaScri...
Meta Keywords: url, console, log, javascript, myurl
-->

# JavaScript 中的 URL：完整指南

## 概述
在 JavaScript 中，URL（統一資源定位符）是用來標識和定位網絡資源的字符串。URL 不僅在網頁中導航至不同的資源，還在 AJAX 請求、API 呼叫等操作中扮演關鍵角色。

## 文檔
### 目的
URL 在 JavaScript 中的主要目的是提供一種方式來表示網絡資源的位置。開發者可以使用 URL 來獲取資料、發送請求，或是導向用戶至特定的網頁。

### 使用方式
JavaScript 提供了 `URL` 和 `URLSearchParams` 兩個內建對象來處理 URL。

- **URL 對象**：用於解析和操作 URL。可以通過 `new URL(urlString)` 創建一個 URL 對象。
- **URLSearchParams 對象**：用於處理 URL 查詢字符串中的參數。

### 詳細說明
```javascript
// 創建一個新的 URL 對象
const myURL = new URL('https://example.com:8000/path?query=123#fragment');

// 獲取不同部分的 URL
console.log(myURL.protocol); // "https:"
console.log(myURL.host);     // "example.com:8000"
console.log(myURL.pathname); // "/path"
console.log(myURL.search);   // "?query=123"
console.log(myURL.hash);     // "#fragment"

// 使用 URLSearchParams 解析查詢字符串
const params = new URLSearchParams(myURL.search);
console.log(params.get('query')); // "123"
```

## 範例
### 基本用法
```javascript
// 創建 URL 對象
const url = new URL('https://www.example.com?name=John&age=30');

// 獲取 URL 參數
console.log(url.hostname); // "www.example.com"
console.log(url.searchParams.get('name')); // "John"

// 修改 URL 參數
url.searchParams.set('age', '31');
console.log(url.toString()); // "https://www.example.com?name=John&age=31"
```

## 解釋
在使用 URL 時，開發者需注意以下幾點：
- URL 的格式必須正確，否則創建 URL 對象會拋出錯誤。
- 使用 `URLSearchParams` 時，必須小心處理重複的參數，因為它會返回第一個匹配的值。
- 當處理包含特殊字符的 URL 時，確保進行適當的編碼（使用 `encodeURIComponent` 和 `decodeURIComponent`）。

## 總結
URL 在 JavaScript 中是定位和操作網絡資源的核心工具，掌握其用法對於網頁開發至關重要。