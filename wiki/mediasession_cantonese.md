<!--
Meta Description: # MediaSession: 使用 JavaScript 管理媒體播放狀態 ## 概述 MediaSession 是一個用於控制媒體播放的 API，讓開發者可以自訂媒體播放的行為並提供更好的用戶體驗，特別是在移動設備上。這個 API 使得媒體控制更加簡單且直觀。 ## 文檔 ### 目的 Medi...
Meta Keywords: mediasession, api, navigator, javascript, setactionhandler
-->

# MediaSession: 使用 JavaScript 管理媒體播放狀態

## 概述
MediaSession 是一個用於控制媒體播放的 API，讓開發者可以自訂媒體播放的行為並提供更好的用戶體驗，特別是在移動設備上。這個 API 使得媒體控制更加簡單且直觀。

## 文檔
### 目的
MediaSession API 旨在讓開發者能夠為其網頁應用提供媒體播放的控制功能，並能夠在操作系統層級（例如鎖屏或媒體控制中心）顯示媒體信息。

### 使用方法
使用 MediaSession API 需要首先檢查瀏覽器是否支持它，然後設置一些屬性來提供媒體的元數據和控制功能。以下是基本的使用步驟：

1. **檢查支持性**：
   ```javascript
   if ('mediaSession' in navigator) {
       console.log('MediaSession is supported');
   }
   ```

2. **設置媒體元數據**：
   ```javascript
   navigator.mediaSession.metadata = new MediaMetadata({
       title: '歌曲標題',
       artist: '藝術家名稱',
       album: '專輯名稱',
       artwork: [
           { src: '封面圖像網址', sizes: '512x512', type: 'image/png' }
       ]
   });
   ```

3. **設置媒體控制事件**：
   ```javascript
   navigator.mediaSession.setActionHandler('play', function() {
       // 播放音樂的邏輯
   });

   navigator.mediaSession.setActionHandler('pause', function() {
       // 暫停音樂的邏輯
   });
   ```

### 詳細信息
MediaSession API 包含的主要特性包括：
- `metadata`：用於設置媒體的標題、藝術家、專輯和封面圖像。
- `setActionHandler(action, handler)`：用於設置對應的媒體控制行為（如播放、暫停、快進等）的回調函數。

## 範例
以下是一個簡單的範例，展示如何使用 MediaSession API 來控制音樂播放：

```javascript
if ('mediaSession' in navigator) {
    navigator.mediaSession.metadata = new MediaMetadata({
        title: '我的歌曲',
        artist: '我的藝術家',
        album: '我的專輯',
        artwork: [
            { src: 'https://example.com/artwork.jpg', sizes: '512x512', type: 'image/jpeg' }
        ]
    });

    navigator.mediaSession.setActionHandler('play', function() {
        console.log('播放音樂');
        // 播放邏輯
    });

    navigator.mediaSession.setActionHandler('pause', function() {
        console.log('暫停音樂');
        // 暫停邏輯
    });
}
```

## 解釋
在使用 MediaSession API 時，開發者需要注意以下幾點：
- 確保瀏覽器支持 MediaSession API，否則相關功能將無法運行。
- 媒體元數據的更新需要在播放狀態變化時進行，以保持信息的準確性。
- 不同平台對於媒體控制的支持程度不同，開發者應該進行充分的測試。

## 一句總結
MediaSession API 提供了一個簡單的方式來管理媒體播放狀態，增強了用戶的媒體體驗。