<!--
Meta Description: # PushManager: JavaScript 中的推送管理器 ## 概述 PushManager 是一个 Web API 接口，允许开发者与浏览器的推送通知系统进行交互。通过 PushManager，开发者可以订阅和管理推送消息，以便向用户发送实时通知，增强用户体验。 ## 文档 ### 目的...
Meta Keywords: pushmanager, api, console, push, log
-->

# PushManager: JavaScript 中的推送管理器

## 概述
PushManager 是一个 Web API 接口，允许开发者与浏览器的推送通知系统进行交互。通过 PushManager，开发者可以订阅和管理推送消息，以便向用户发送实时通知，增强用户体验。

## 文档
### 目的
PushManager 主要用于处理推送通知的订阅和管理。它提供了一种机制，允许网页应用在用户不直接与其交互时，仍然能够向用户发送重要信息。

### 用法
要使用 PushManager，首先需要确保用户的浏览器支持该功能，并且用户已经允许网站发送通知。以下是使用 PushManager 的基本步骤：

1. **检查支持性**：确保浏览器支持 Push API。
2. **请求权限**：向用户请求通知权限。
3. **订阅推送**：使用 PushManager 创建一个新的推送订阅。
4. **管理订阅**：可以查看、更新或取消订阅。

#### 示例代码
```javascript
// 检查是否支持 Push API
if ('serviceWorker' in navigator && 'PushManager' in window) {
    console.log('Push API is supported.');

    // 请求通知权限
    Notification.requestPermission().then(permission => {
        if (permission === 'granted') {
            console.log('Notification permission granted.');

            // 注册 Service Worker
            navigator.serviceWorker.register('/sw.js').then(registration => {
                // 订阅推送
                registration.pushManager.subscribe({
                    userVisibleOnly: true, // 需要显示通知
                    applicationServerKey: urlBase64ToUint8Array('<YOUR_PUBLIC_VAPID_KEY>')
                }).then(subscription => {
                    console.log('User is subscribed:', subscription);
                }).catch(err => {
                    console.warn('Failed to subscribe the user: ', err);
                });
            });
        } else {
            console.log('Notification permission denied.');
        }
    });
} else {
    console.log('Push API is not supported in this browser.');
}

// 辅助函数：将 VAPID 密钥从 Base64 转换为 Uint8Array
function urlBase64ToUint8Array(base64String) {
    const padding = '='.repeat((4 - base64String.length % 4) % 4);
    const base64 = (base64String + padding).replace(/-/g, '+').replace(/_/g, '/');
    const rawData = window.atob(base64);
    return new Uint8Array([...rawData].map(char => char.charCodeAt(0)));
}
```

## 说明
- **权限管理**：用户必须首先允许通知权限，否则无法使用 PushManager。
- **Service Worker**：PushManager 依赖于 Service Worker，因此必须确保在使用 PushManager 之前注册 Service Worker。
- **订阅选项**：在订阅时，可以设置 `userVisibleOnly` 属性，强制要求推送通知必须是可见的。

### 常见问题
- **用户未授权**：在未获得用户允许的情况下，尝试订阅推送会失败。
- **浏览器兼容性**：并非所有浏览器都支持 Push API，因此在实现时需要考虑兼容性。
- **网络问题**：推送通知的接收依赖于网络状态，网络不稳定可能导致通知延迟或丢失。

## 一句话总结
PushManager 是一个用于管理和发送推送通知的 JavaScript API，增强了用户与网页应用的交互体验。