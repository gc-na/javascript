<!--
Meta Description: # PushSubscription 在 JavaScript 中的應用 ## 概述 PushSubscription 是一個與 Web Push 訊息相關的介面，允許網頁應用程式訂閱推送通知。這使得開發者能夠在用戶不主動訪問網站時，仍能向用戶發送訊息。 ## 文檔 ### 目的 PushSubsc...
Meta Keywords: pushsubscription, function, subscription, console, log
-->

# PushSubscription 在 JavaScript 中的應用

## 概述
PushSubscription 是一個與 Web Push 訊息相關的介面，允許網頁應用程式訂閱推送通知。這使得開發者能夠在用戶不主動訪問網站時，仍能向用戶發送訊息。

## 文檔
### 目的
PushSubscription 的主要目的是通過服務工作者 (Service Worker) 管理推送通知的訂閱。它是 Web Push API 的一部分，提供了一種有效的方式來發送實時通知，使得用戶能夠保持更新。

### 使用方法
要使用 PushSubscription，開發者需執行以下步驟：

1. **訂閱推送通知**：
   使用 `PushManager.subscribe()` 方法來請求用戶的訂閱權限。

   ```javascript
   navigator.serviceWorker.ready.then(function(registration) {
       return registration.pushManager.subscribe({
           userVisibleOnly: true,
           applicationServerKey: '<Your Public VAPID Key>'
       });
   }).then(function(subscription) {
       console.log('User is subscribed:', subscription);
   }).catch(function(err) {
       console.log('Failed to subscribe the user: ', err);
   });
   ```

2. **管理訂閱**：
   PushSubscription 提供方法來獲取訂閱的詳細資訊，例如端點 URL 和主密鑰。

   ```javascript
   console.log('Endpoint:', subscription.endpoint);
   console.log('Keys:', subscription.getKey('p256dh'), subscription.getKey('auth'));
   ```

3. **取消訂閱**：
   用戶也可以隨時取消訂閱，這可以通過 `unsubscribe()` 方法實現。

   ```javascript
   subscription.unsubscribe().then(function(successful) {
       console.log('User is unsubscribed:', successful);
   }).catch(function(err) {
       console.log('Failed to unsubscribe the user: ', err);
   });
   ```

### 詳細資訊
- **屬性**：
  - `endpoint`：推送服務的 URL。
  - `expirationTime`：訂閱的過期時間，若無限制則為 `null`。
  - `keys`：包含 `p256dh` 和 `auth` 密鑰，這些密鑰用於加密推送訊息。

- **方法**：
  - `getKey(name)`：返回指定名稱的加密密鑰。

## 範例
以下是基本的 PushSubscription 使用範例：

```javascript
// 訂閱推送通知
navigator.serviceWorker.register('sw.js').then(function(registration) {
   return registration.pushManager.subscribe({
       userVisibleOnly: true,
       applicationServerKey: '<Your Public VAPID Key>'
   });
}).then(function(subscription) {
   console.log('訂閱成功:', subscription);
}).catch(function(err) {
   console.error('訂閱失敗:', err);
});
```

## 解釋
在使用 PushSubscription 時，有幾個常見的問題需要注意：

- **用戶授權**：請確保用戶已授權接收推送通知，否則訂閱將會失敗。
- **服務工作者**：PushSubscription 必須在服務工作者的上下文中操作，這意味著在頁面中註冊服務工作者是必要的。
- **VAPID 金鑰**：確保使用有效的 VAPID 公鑰進行訂閱，這是用於身份驗證的。

## 一句話總結
PushSubscription 是一個 JavaScript 接口，允許開發者管理用戶的推送通知訂閱，增強用戶互動性和消息傳遞能力。