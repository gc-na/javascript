<!--
Meta Description: # PushSubscription：JavaScript 中的推送订阅 ## 概要 PushSubscription 是 Web Push API 的一部分，它允许开发者在用户的浏览器中注册推送通知。这使得网站能够在用户未打开页面时向其发送实时更新和消息。 ## 文档 ### 目的 PushSub...
Meta Keywords: error, function, pushsubscription, push, console
-->

# PushSubscription：JavaScript 中的推送订阅

## 概要
PushSubscription 是 Web Push API 的一部分，它允许开发者在用户的浏览器中注册推送通知。这使得网站能够在用户未打开页面时向其发送实时更新和消息。

## 文档

### 目的
PushSubscription 主要用于管理用户的推送通知订阅。通过该接口，开发者可以创建、更新和删除用户的订阅，从而实现实时消息推送功能。

### 用法
1. **注册推送订阅**：使用 `Service Worker` 和 `PushManager` 接口创建新的推送订阅。
2. **处理推送通知**：通过监听 `push` 事件处理收到的推送消息。
3. **取消订阅**：允许用户随时取消订阅以停止接收推送通知。

### 详细信息
- **属性**：
  - `endpoint`: 订阅的唯一标识符，用于推送通知的目标。
  - `expirationTime`: 订阅的过期时间（如果未设置则为 null）。
  - `keys`: 包含用于加密和解密的公钥和私钥。

- **方法**：
  - `unsubscribe()`: 取消当前的推送订阅。

## 示例

### 注册推送订阅
```javascript
navigator.serviceWorker.register('/sw.js').then(function(registration) {
    return registration.pushManager.subscribe({
        userVisibleOnly: true,
        applicationServerKey: urlB64ToUint8Array('YOUR_PUBLIC_VAPID_KEY')
    });
}).then(function(subscription) {
    console.log('User is subscribed:', subscription);
}).catch(function(error) {
    console.error('Failed to subscribe the user: ', error);
});
```

### 取消订阅
```javascript
subscription.unsubscribe().then(function(successful) {
    console.log('Unsubscribed successfully:', successful);
}).catch(function(error) {
    console.error('Failed to unsubscribe: ', error);
});
```

## 解释
- **常见陷阱**：
  - 确保用户的浏览器支持推送通知。并非所有浏览器都支持 Web Push API。
  - 在注册推送订阅之前，必须先注册一个 Service Worker。
  - 处理订阅的权限请求，确保用户允许接收通知。

- **注意事项**：
  - 订阅的 `endpoint` 是特定于浏览器和设备的，不能在不同平台之间共享。
  - 在发送推送通知时，需要使用正确的 VAPID 密钥进行身份验证。
  - 如果过期时间设置为 null，订阅将不会自动过期。

## 一句话总结
PushSubscription 是 Web Push API 中用于管理用户推送通知订阅的接口。