<!--
Meta Description: # WakeLockSentinel 在 JavaScript 中的應用 ## 概述 WakeLockSentinel 是一個 Web API，用於管理設備的喚醒鎖，旨在防止設備進入休眠狀態，從而在執行需要持續顯示的任務時保持屏幕亮起。 ## 文檔 ### 目的 WakeLockSentinel 提...
Meta Keywords: wakelock, wakelocksentinel, javascript, await, release
-->

# WakeLockSentinel 在 JavaScript 中的應用

## 概述
WakeLockSentinel 是一個 Web API，用於管理設備的喚醒鎖，旨在防止設備進入休眠狀態，從而在執行需要持續顯示的任務時保持屏幕亮起。

## 文檔
### 目的
WakeLockSentinel 提供了一種方法來保持設備的屏幕活躍，這在需要長時間顯示內容的應用中非常有用，例如在線會議、電子書閱讀器或任何需要持續用戶交互的應用。

### 使用方式
要使用 WakeLockSentinel，首先需要請求喚醒鎖。這可以通過 `navigator.wakeLock.request()` 方法來完成。此方法返回一個 Promise，解析為一個 WakeLockSentinel 實例，該實例可用於釋放喚醒鎖。

#### 基本語法
```javascript
const wakeLock = await navigator.wakeLock.request('screen');
```

#### 釋放喚醒鎖
當不再需要保持屏幕活躍時，可以通過呼叫 `release()` 方法來釋放喚醒鎖：
```javascript
await wakeLock.release();
```

### 詳細說明
- **請求喚醒鎖**: 當請求喚醒鎖成功時，會返回一個 WakeLockSentinel 物件。這個物件可以用來檢查當前的喚醒鎖狀態。
- **釋放喚醒鎖**: 當不再需要喚醒鎖時，應立即釋放它，這樣可以節省電池壽命。
- **錯誤處理**: 如果設備不支持此功能，或請求失敗，應該適當地處理錯誤。

## 範例
### 請求喚醒鎖
```javascript
async function requestWakeLock() {
    try {
        const wakeLock = await navigator.wakeLock.request('screen');
        console.log('喚醒鎖已獲取');
        
        // 在需要的時候釋放喚醒鎖
        // await wakeLock.release();
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

requestWakeLock();
```

### 釋放喚醒鎖
```javascript
async function releaseWakeLock(wakeLock) {
    if (wakeLock) {
        await wakeLock.release();
        console.log('喚醒鎖已釋放');
    }
}
```

## 解釋
- **常見錯誤**: 忘記釋放喚醒鎖可能會導致設備電池快速耗盡，因此在不需要時應務必釋放。
- **支持性**: 並非所有瀏覽器都支持 WakeLock API，因此在使用之前應檢查支持性。
- **用戶許可**: 在某些情況下，可能需要用戶的許可才能獲取喚醒鎖，確保遵循最佳實踐。

## 總結
WakeLockSentinel 是一個強大的工具，能夠讓開發者在需要時保持設備屏幕活躍，從而提升用戶體驗。