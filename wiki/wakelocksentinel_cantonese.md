<!--
Meta Description: # WakeLockSentinel：JavaScript 中的螢幕鎖定控制 ## Synopsis WakeLockSentinel 是一個 JavaScript 介面，允許開發者控制裝置的螢幕鎖定狀態，以確保在特定情況下螢幕不會進入休眠或關閉狀態，特別適合需要長時間顯示內容的應用程式。 ## D...
Meta Keywords: wakelocksentinel, wakelock, javascript, console, err
-->

# WakeLockSentinel：JavaScript 中的螢幕鎖定控制

## Synopsis
WakeLockSentinel 是一個 JavaScript 介面，允許開發者控制裝置的螢幕鎖定狀態，以確保在特定情況下螢幕不會進入休眠或關閉狀態，特別適合需要長時間顯示內容的應用程式。

## Documentation
### 目的
WakeLockSentinel 的主要目的是防止裝置在指定的時間內進入休眠狀態，這對於如視頻播放、即時通訊或任何需要用戶持續關注的應用程式非常重要。

### 使用方法
要使用 WakeLockSentinel，開發者必須首先請求一個螢幕鎖定，然後可以通過該物件來控制鎖定狀態。

### 主要方法
- `navigator.wakeLock.request(type)`：請求一個指定類型的鎖定，返回一個 WakeLockSentinel 實例。
- `release()`：釋放當前的鎖定，允許裝置進入休眠。

### 支援的類型
- `'screen'`：螢幕鎖定，用來防止螢幕關閉。

## Examples
### 基本使用範例
```javascript
async function requestWakeLock() {
    try {
        const wakeLock = await navigator.wakeLock.request('screen');
        console.log('螢幕鎖定已啟動');

        // 在這裡可以進行需要螢幕不關閉的操作

        // 當不再需要鎖定時，釋放鎖定
        await wakeLock.release();
        console.log('螢幕鎖定已釋放');
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

requestWakeLock();
```

## Explanation
### 常見問題
- **庫存狀態**：當請求鎖定後，應儘早釋放鎖定，以避免影響用戶的裝置使用體驗。
- **相容性**：並非所有瀏覽器都支援 WakeLock API，請確認您的目標瀏覽器相容性。
- **用戶互動**：一些瀏覽器可能要求在用戶互動（如點擊或按鍵）後才能啟用鎖定。

### 注意事項
- 應避免在不必要的情況下使用螢幕鎖定，以節省電池壽命。
- 在網頁重新載入或關閉時，鎖定會自動釋放。

## One Line Summary
WakeLockSentinel 是一個 JavaScript 介面，用於防止裝置螢幕進入休眠狀態，確保應用程式持續可見。