<!--
Meta Description: # WakeLock 在 JavaScript 中的應用 ## 概述 WakeLock 是一項 Web API，允許開發者在使用者的設備上保持螢幕常亮，以防止其進入休眠狀態，從而提升用戶體驗，特別是在需要長時間顯示資訊的應用中。 ## 文檔 ### 目的 WakeLock API 的主要目的是解決移...
Meta Keywords: wakelock, api, await, javascript, navigator
-->

# WakeLock 在 JavaScript 中的應用

## 概述
WakeLock 是一項 Web API，允許開發者在使用者的設備上保持螢幕常亮，以防止其進入休眠狀態，從而提升用戶體驗，特別是在需要長時間顯示資訊的應用中。

## 文檔
### 目的
WakeLock API 的主要目的是解決移動設備在進行某些操作（如觀看影片或進行遊戲）時自動進入休眠狀態的問題，從而保證用戶能夠持續互動而不會被中斷。

### 使用方法
使用 WakeLock API 需要透過 `navigator.wakeLock.request()` 方法來請求保持螢幕常亮的權限。此方法會返回一個 Promise，當請求成功時，會返回一個 WakeLock 物件。

#### 基本語法：
```javascript
let wakeLock = null;

async function requestWakeLock() {
    try {
        wakeLock = await navigator.wakeLock.request("screen");
        console.log("Wake Lock is active.");
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

async function releaseWakeLock() {
    if (wakeLock !== null) {
        await wakeLock.release();
        wakeLock = null;
        console.log("Wake Lock has been released.");
    }
}
```

### 細節
- **請求螢幕鎖定**: 使用 `navigator.wakeLock.request(type)` 請求指定類型的 WakeLock，`type` 目前只支持 "screen"。
- **釋放螢幕鎖定**: 使用 `wakeLock.release()` 方法來釋放已持有的 WakeLock。
- **錯誤處理**: 在請求或釋放 WakeLock 時，需進行適當的錯誤處理，以應對可能的拒絕狀態或不支援情況。

## 示例
以下是幾個簡單的使用範例：

### 基本範例
```javascript
document.getElementById("start").addEventListener("click", requestWakeLock);
document.getElementById("stop").addEventListener("click", releaseWakeLock);
```

### 異步請求與釋放
```javascript
async function handleWakeLock() {
    await requestWakeLock();
    // 執行其他任務
    await new Promise(resolve => setTimeout(resolve, 10000)); // 模擬任務持續10秒
    await releaseWakeLock();
}

handleWakeLock();
```

## 說明
### 常見問題
- **不支援的瀏覽器**: 目前並非所有瀏覽器都支持 WakeLock API，建議在開發前查閱支持情況。
- **權限問題**: 若用戶拒絕了 WakeLock 請求，開發者需提供清晰的錯誤處理機制，以改善使用體驗。
- **多次請求**: 不要在未釋放的情況下多次請求 WakeLock，這可能會導致錯誤或不預期的行為。

## 總結
WakeLock API 是一個強大的工具，能夠提升 Web 應用的用戶體驗，透過保持螢幕亮度來確保用戶的互動不會中斷。