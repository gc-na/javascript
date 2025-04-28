<!--
Meta Description: # WakeLock 在 JavaScript 中的應用 ## 簡介 WakeLock 是一項使用於 JavaScript 的功能，旨在讓開發者能夠防止設備進入睡眠狀態，以提升用戶體驗，特別是在需要長時間顯示信息的應用中。 ## 文檔 ### 目的 WakeLock API 允許開發者控制設備的螢幕...
Meta Keywords: wakelock, api, javascript, console, log
-->

# WakeLock 在 JavaScript 中的應用

## 簡介
WakeLock 是一項使用於 JavaScript 的功能，旨在讓開發者能夠防止設備進入睡眠狀態，以提升用戶體驗，特別是在需要長時間顯示信息的應用中。

## 文檔
### 目的
WakeLock API 允許開發者控制設備的螢幕狀態，防止其自動熄滅。這在需要持續顯示的情境下特別有用，例如視頻播放、遊戲或實時數據顯示。

### 使用方法
要使用 WakeLock API，你需要執行以下步驟：

1. 檢查瀏覽器是否支持 WakeLock API：
   ```javascript
   if ('wakeLock' in navigator) {
       console.log('WakeLock API is supported!');
   } else {
       console.log('WakeLock API is not supported on this browser.');
   }
   ```

2. 請求 WakeLock：
   ```javascript
   let wakeLock = null;

   async function requestWakeLock() {
       try {
           wakeLock = await navigator.wakeLock.request('screen');
           console.log('Wake Lock is active!');
       } catch (err) {
           console.error(`${err.name}, ${err.message}`);
       }
   }
   ```

3. 釋放 WakeLock：
   ```javascript
   async function releaseWakeLock() {
       if (wakeLock !== null) {
           await wakeLock.release();
           wakeLock = null;
           console.log('Wake Lock has been released.');
       }
   }
   ```

### 詳細信息
- **請求類型**：目前 WakeLock API 支持的請求類型有 'screen' 和 'system'。通常我們使用 'screen' 來保持螢幕亮起。
- **瀏覽器支持**：並非所有瀏覽器都支持 WakeLock API，建議在使用前進行檢查。
- **資源管理**：確保在不需要時釋放 WakeLock，以避免影響設備電池壽命。

## 範例
這裡是一個簡單的範例，展示如何使用 WakeLock API 來保持螢幕亮起：

```javascript
document.getElementById('activateWakeLock').addEventListener('click', requestWakeLock);
document.getElementById('deactivateWakeLock').addEventListener('click', releaseWakeLock);
```

### HTML 範例
```html
<button id="activateWakeLock">啟用 Wake Lock</button>
<button id="deactivateWakeLock">釋放 Wake Lock</button>
```

## 解釋
### 常見問題
- **不支持的瀏覽器**：如果用戶的瀏覽器不支持 WakeLock API，請確保有適當的回退方案。
- **電池消耗**：長時間保持 WakeLock 會對設備電池造成影響，應根據需求合理使用。

### 注意事項
- 使用 WakeLock 時，需注意用戶的隱私和經驗，避免在不必要的情況下保持螢幕常亮。
- 在移動設備上測試功能，以確保其行為符合預期。

## 單行摘要
WakeLock API 允許 JavaScript 開發者在需要時防止設備螢幕進入睡眠狀態，提升用戶體驗。