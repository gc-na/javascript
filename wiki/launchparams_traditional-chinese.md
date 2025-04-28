<!--
Meta Description: # LaunchParams：JavaScript 中的啟動參數 ## 概述 LaunchParams 是一個在 JavaScript 中用於獲取應用程序啟動參數的功能，特別是在 Web 應用和瀏覽器環境中。這些參數可以幫助開發者在應用啟動時獲取必要的信息，以便進行相應的配置或初始化。 ## 文檔 ...
Meta Keywords: userid, javascript, params, theme, launchparams
-->

# LaunchParams：JavaScript 中的啟動參數

## 概述
LaunchParams 是一個在 JavaScript 中用於獲取應用程序啟動參數的功能，特別是在 Web 應用和瀏覽器環境中。這些參數可以幫助開發者在應用啟動時獲取必要的信息，以便進行相應的配置或初始化。

## 文檔
### 目的
LaunchParams 的主要目的是提供一種簡單的方法來獲取應用程序啟動時傳遞的參數，這對於需要根據不同情境進行定制的應用尤為重要。

### 使用方法
在 JavaScript 中，LaunchParams 通常通過 `window.location` 或 `URLSearchParams` 進行訪問。使用者可以解析 URL 中的查詢參數來獲取啟動參數。

#### 代碼範例
```javascript
// 使用 URLSearchParams 來獲取啟動參數
const params = new URLSearchParams(window.location.search);

// 獲取特定的啟動參數
const userId = params.get('userId'); // 假設 URL 中有 ?userId=123
console.log(userId); // 輸出: 123
```

## 示例
### 基本用法
假設我們有一個 URL 如下：
```
https://example.com?userId=123&theme=dark
```
我們可以使用以下代碼獲取 `userId` 和 `theme` 參數：
```javascript
const params = new URLSearchParams(window.location.search);
const userId = params.get('userId'); // 獲取 userId
const theme = params.get('theme'); // 獲取主題
console.log(`User ID: ${userId}, Theme: ${theme}`); // 輸出: User ID: 123, Theme: dark
```

### 錯誤處理示例
在獲取啟動參數時，開發者應確保檢查參數是否存在：
```javascript
const userId = params.get('userId');
if (userId) {
    console.log(`User ID: ${userId}`);
} else {
    console.error('User ID is not provided.');
}
```

## 解釋
在使用 LaunchParams 時，開發者可能會遇到一些常見的陷阱，例如：

1. **參數不存在**：如果請求的參數不在 URL 中，則返回的值將為 `null`，開發者應該進行檢查。
   
2. **編碼問題**：URL 中的特殊字符需要進行編碼，否則將無法正確獲取參數值。

3. **大小寫敏感**：查詢參數是大小寫敏感的，`userid` 和 `userId` 被視為不同的參數。

4. **多個同名參數**：如果 URL 中有多個同名參數，`get` 方法僅返回第一個值。可以使用 `params.getAll('paramName')` 獲取所有匹配的值。

## 一行總結
LaunchParams 是 JavaScript 中用於獲取應用啟動參數的工具，幫助開發者進行動態配置。