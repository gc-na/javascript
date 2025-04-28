<!--
Meta Description: # StorageEvent: JavaScript 中的儲存事件 ## 概述 `StorageEvent` 是一個重要的 JavaScript 事件，用於監聽和響應 Web Storage（如 localStorage 和 sessionStorage）中的變更。當另一個窗口或標籤頁對儲存進行更改...
Meta Keywords: storageevent, event, javascript, console, log
-->

# StorageEvent: JavaScript 中的儲存事件

## 概述
`StorageEvent` 是一個重要的 JavaScript 事件，用於監聽和響應 Web Storage（如 localStorage 和 sessionStorage）中的變更。當另一個窗口或標籤頁對儲存進行更改時，`StorageEvent` 將被觸發，這對於需要跨窗口或標籤頁同步狀態的應用程式非常有用。

## 文檔
### 目的
`StorageEvent` 主要用於監聽在同一源（origin）下的儲存變化事件。這使得開發者能夠在多個窗口或標籤頁之間共享資料，並及時更新應用程式的狀態。

### 用法
當儲存資料被修改時，`StorageEvent` 會被觸發。這個事件會包含一些有用的屬性，例如：
- `key`: 被修改的儲存鍵。
- `newValue`: 新的值。
- `oldValue`: 修改前的舊值。
- `url`: 觸發事件的頁面 URL。
- `storageArea`: 觸發事件的儲存區域（localStorage 或 sessionStorage）。

事件的監聽方式如下：
```javascript
window.addEventListener('storage', function(event) {
    console.log('Storage key changed:', event.key);
    console.log('New Value:', event.newValue);
    console.log('Old Value:', event.oldValue);
    console.log('Source URL:', event.url);
});
```

## 範例
以下是使用 `StorageEvent` 的基本範例：

### 基本範例：
1. **在一個窗口中設置儲存**：
```javascript
localStorage.setItem('username', 'JohnDoe');
```

2. **在另一個窗口中監聽儲存事件**：
```javascript
window.addEventListener('storage', function(event) {
    if (event.key === 'username') {
        console.log('Username updated to:', event.newValue);
    }
});
```

### 使用情境：
假設有兩個標籤頁，當在第一個標籤頁更新 `username` 時，第二個標籤頁會即時接收到變更。

## 解釋
### 常見問題和注意事項
- `StorageEvent` 僅在不同的窗口或標籤頁之間觸發。對於同一窗口的儲存變更，不會觸發此事件。
- 事件只會在同一源的窗口之間傳遞，這意味著如果跨不同的域名或協議，則不會觸發事件。
- 在監聽事件時，應注意可能的性能問題，尤其是在高頻率的儲存操作下。

## 總結
`StorageEvent` 是 JavaScript 中一個強大的工具，允許開發者在多個窗口或標籤頁之間有效地管理和同步儲存資料。