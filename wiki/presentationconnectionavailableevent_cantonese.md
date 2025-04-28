<!--
Meta Description: # PresentationConnectionAvailableEvent：JavaScript 中的演示連接可用事件 ## 簡介 `PresentationConnectionAvailableEvent` 是一個在 JavaScript 中用於處理演示連接可用性的事件。這個事件是 Web 演示...
Meta Keywords: presentation, presentationconnectionavailableevent, javascript, navigator, function
-->

# PresentationConnectionAvailableEvent：JavaScript 中的演示連接可用事件

## 簡介
`PresentationConnectionAvailableEvent` 是一個在 JavaScript 中用於處理演示連接可用性的事件。這個事件是 Web 演示 API 的一部分，可以讓開發者在設備之間建立和管理媒體流連接，從而支援多媒體內容的無縫播放。

## 文檔
### 目的
`PresentationConnectionAvailableEvent` 的主要目的是通知應用程式當有新的可用演示連接時。這對於需要在不同設備之間分享內容的應用程式尤為重要，例如投影儀或智能電視。

### 使用方法
要使用 `PresentationConnectionAvailableEvent`，你需要監聽 `navigator.presentation` 對象的 `connectionavailable` 事件。當新的演示連接可用時，事件將被觸發，並提供相關的事件物件。

### 事件屬性
- **connection**：返回一個 `PresentationConnection` 對象，代表可用的演示連接。

### 事件監聽器
以下是如何添加事件監聽器的範例：

```javascript
navigator.presentation.addEventListener('connectionavailable', function(event) {
    console.log('新的演示連接可用:', event.connection);
});
```

## 範例
以下是一個簡單的使用範例：

```javascript
if (navigator.presentation) {
    navigator.presentation.addEventListener('connectionavailable', function(event) {
        console.log('可用的演示連接:', event.connection);
    });

    // 嘗試啟動演示
    navigator.presentation.requestPresentation().then(function(presentation) {
        console.log('演示已啟動:', presentation);
    }).catch(function(error) {
        console.error('啟動演示失敗:', error);
    });
}
```

## 解釋
在使用 `PresentationConnectionAvailableEvent` 時，開發者需要注意以下幾點：
- 確保瀏覽器支持 Web 演示 API，否則事件將無法觸發。
- 事件的觸發取決於設備的連接狀態，可能會受到網絡環境的影響。
- 處理事件時，要考慮到用戶的隱私和安全，避免無意中洩露敏感信息。

## 一句總結
`PresentationConnectionAvailableEvent` 是一個用於在 JavaScript 中處理演示連接可用性的重要事件，幫助開發者在不同設備之間共享內容。