<!--
Meta Description: # 網路資訊 (NetworkInformation) 在 JavaScript 中的應用 ## 概述 `NetworkInformation` 是一個 Web API，提供有關網路連接狀況的資訊。使用者可以透過這個 API 獲取連接類型、有效性等信息，便於根據網路狀況調整應用的行為。 ## 文檔 ...
Meta Keywords: networkinformation, connection, api, console, log
-->

# 網路資訊 (NetworkInformation) 在 JavaScript 中的應用

## 概述
`NetworkInformation` 是一個 Web API，提供有關網路連接狀況的資訊。使用者可以透過這個 API 獲取連接類型、有效性等信息，便於根據網路狀況調整應用的行為。

## 文檔
### 目的
`NetworkInformation` 接口主要用於獲取網路狀態的資訊，幫助開發者根據用戶的網路環境做出相應的決策。這在優化應用效能和改善用戶體驗方面非常重要。

### 用法
要使用 `NetworkInformation`，開發者可以訪問 `navigator.connection` 屬性。這個屬性返回一個 `NetworkInformation` 對象，該對象提供下列屬性和方法：

- **type**: 返回當前的網路連接類型（例如：`wifi`、`cellular`、`none`等）。
- **effectiveType**: 返回網路的有效類型，這基於目前的連接速度（例如：`slow-2g`、`2g`、`3g`、`4g`）。
- **downlink**: 返回用戶的下行帶寬（以 Mbps 為單位）。
- **rtt**: 返回網路的往返時間（以毫秒為單位）。
- **addEventListener**: 用於監聽網路狀態改變的事件。

### 使用範例
以下是 `NetworkInformation` 的基本使用範例：

```javascript
// 獲取網路資訊
const connection = navigator.connection || navigator.mozConnection || navigator.webkitConnection;

if (connection) {
    console.log('連接類型:', connection.type);
    console.log('有效類型:', connection.effectiveType);
    console.log('下行帶寬:', connection.downlink, 'Mbps');
    console.log('往返時間:', connection.rtt, 'ms');

    // 監聽網路狀態改變
    connection.addEventListener('change', () => {
        console.log('網路狀態改變:', connection.type);
    });
} else {
    console.log('該瀏覽器不支持 NetworkInformation API');
}
```

## 解釋
在使用 `NetworkInformation` 時，有一些常見的陷阱和注意事項：

1. **相容性問題**: 並非所有的瀏覽器都支持 `NetworkInformation` API，開發者應該檢查用戶的瀏覽器是否支持此 API。
2. **隱私考量**: 由於涉及網路狀態的資訊，某些瀏覽器可能會對這些資訊的訪問進行限制，以保護用戶隱私。
3. **事件監聽**: 當使用 `addEventListener` 監聽連接變化時，開發者需確保正確處理事件，避免重複註冊相同的事件處理器。

## 一句總結
`NetworkInformation` API 提供了有關用戶網路狀態的關鍵資訊，幫助開發者針對不同的網路環境優化應用體驗。