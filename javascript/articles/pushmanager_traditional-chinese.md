<!--
Meta Description: # PushManager：JavaScript 推播管理器 ## 摘要 PushManager 是一個 Web API，允許開發者與用戶的推播通知進行交互。透過這個 API，開發者可以訂閱、管理和發送推播通知，增強用戶體驗。 ## 文檔 PushManager 是 Service Worker 的...
Meta Keywords: pushmanager, function, subscription, console, service
-->

# PushManager：JavaScript 推播管理器

## 摘要
PushManager 是一個 Web API，允許開發者與用戶的推播通知進行交互。透過這個 API，開發者可以訂閱、管理和發送推播通知，增強用戶體驗。

## 文檔
PushManager 是 Service Worker 的一部分，主要負責處理推播通知的訂閱和管理。以下是 PushManager 的主要功能和用法：

### 目的
PushManager 的主要目的是讓網站能夠向用戶發送即時通知，即使用戶未在網站上時也能接收。這對於增強用戶互動性和即時信息傳遞非常重要。

### 使用方法
要使用 PushManager，首先需要註冊 Service Worker，然後通過 `navigator.serviceWorker.ready` 確保 Service Worker 已經就緒。接著，可以使用 `PushManager` 進行推播通知的訂閱。

### 詳細說明
1. **訂閱推播通知**：
   ```javascript
   navigator.serviceWorker.ready.then(function(registration) {
       return registration.pushManager.subscribe({
           userVisibleOnly: true,
           applicationServerKey: urlB64ToUint8Array('YOUR_PUBLIC_VAPID_KEY')
       });
   }).then(function(subscription) {
       console.log('User is subscribed:', subscription);
   }).catch(function(err) {
       console.log('Failed to subscribe the user: ', err);
   });
   ```

2. **取消訂閱**：
   訂閱後，用戶也可以選擇取消訂閱：
   ```javascript
   subscription.unsubscribe().then(function(successful) {
       console.log('User is unsubscribed:', successful);
   }).catch(function(err) {
       console.log('Error while unsubscribing', err);
   });
   ```

## 範例
以下是基本的 PushManager 使用範例：

### 註冊 Service Worker 並訂閱推播通知
```javascript
if ('serviceWorker' in navigator && 'PushManager' in window) {
   navigator.serviceWorker.register('/sw.js').then(function(registration) {
       console.log('Service Worker registered with scope:', registration.scope);
       return registration.pushManager.subscribe({
           userVisibleOnly: true,
           applicationServerKey: urlB64ToUint8Array('YOUR_PUBLIC_VAPID_KEY')
       });
   }).then(function(subscription) {
       console.log('Push Subscription:', subscription);
   }).catch(function(error) {
       console.error('Error during service worker registration or push subscription:', error);
   });
}
```

## 解釋
### 常見問題
- **瀏覽器兼容性**：並非所有瀏覽器都支持 PushManager，因此在開發時需要檢查用戶的瀏覽器支持情況。
- **用戶授權**：用戶必須允許推播通知，否則無法成功訂閱。
- **安全性要求**：PushManager 只能在 HTTPS 上運行，這是為了保護用戶的隱私和數據。

### 附加注意事項
- 在發送推播通知時，確保遵循最佳實踐，如提供有意義的內容和適當的頻率，以免用戶感到困擾。
- 使用 VAPID 密鑰進行安全驗證，以保護推播服務。

## 一句話總結
PushManager 是一個強大的 API，讓開發者能夠向用戶發送推播通知，提升網站的互動性和信息傳遞效率。