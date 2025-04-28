<!--
Meta Description: # PresentationReceiver 在 JavaScript 中的使用指南 ## 簡介 PresentationReceiver 是一個 JavaScript API，允許網頁應用程式在 Presentation 環境中接收內容，從而簡化多屏幕互動的過程。這個 API 主要用於開發支持投影...
Meta Keywords: presentationreceiver, api, console, log, navigator
-->

# PresentationReceiver 在 JavaScript 中的使用指南

## 簡介
PresentationReceiver 是一個 JavaScript API，允許網頁應用程式在 Presentation 環境中接收內容，從而簡化多屏幕互動的過程。這個 API 主要用於開發支持投影的應用程式，使其能夠在不同設備之間進行內容共享和控制。

## 文檔
### 目的
PresentationReceiver 主要用來接收和處理來自 Presentation Controller 的媒體流。這個 API 使得網頁應用能夠在投影設備（例如智能電視或投影機）上顯示內容，並能夠接收來自控制設備的指令。

### 使用方法
使用 PresentationReceiver API，開發者可以設置一個接收器來接收來自控制器的請求。以下是基本的使用步驟：

1. 設置接收器：使用 `navigator.presentationReceiver` 來獲取 PresentationReceiver 實例。
2. 監聽事件：註冊適當的事件處理器以響應來自控制器的請求。
3. 處理請求：根據接收到的請求來顯示內容或執行相應的操作。

### 主要屬性和方法
- `navigator.presentationReceiver`: 獲取當前的 PresentationReceiver 實例。
- `onconnectionavailable`: 當有新的控制器連接時觸發的事件。
- `onconnectionclosed`: 當控制器斷開連接時觸發的事件。

## 範例
以下是一個基本的範例，展示如何使用 PresentationReceiver：

```javascript
if (navigator.presentationReceiver) {
    navigator.presentationReceiver.onconnectionavailable = (event) => {
        const connection = event.connection;
        console.log("接收到連接:", connection);
        
        connection.onmessage = (msgEvent) => {
            console.log("接收到消息:", msgEvent.data);
        };

        connection.onclose = () => {
            console.log("連接已關閉");
        };
    };

    navigator.presentationReceiver.onconnectionclosed = (event) => {
        console.log("控制器已斷開連接");
    };

    console.log("PresentationReceiver 已啟用");
} else {
    console.log("瀏覽器不支持 PresentationReceiver API");
}
```

## 解釋
當使用 PresentationReceiver API 時，有幾個常見的陷阱和注意事項：

- **瀏覽器支持**: 並非所有瀏覽器都支持 PresentationReceiver API，因此在使用前應檢查其支持狀態。
- **安全性**: 確保在安全的環境中使用此 API，以防止潛在的安全漏洞。
- **狀態管理**: 在處理連接和消息時，開發者應妥善管理應用的狀態，以避免錯誤的行為。

## 簡要總結
PresentationReceiver 是一個用於在多屏幕環境中接收和顯示內容的 JavaScript API，簡化了設備間的內容共享和互動。