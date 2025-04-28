<!--
Meta Description: # MediaMetadata：JavaScript 中的媒體元數據管理 ## 概要 MediaMetadata 是一個 Web API，允許開發者在網頁中提供媒體內容的元數據，從而改善用戶體驗，尤其是在播放音樂和影片時。它使網站能夠顯示歌曲標題、藝術家、專輯封面等信息。 ## 文檔 ### 目的 ...
Meta Keywords: mediametadata, metadata, api, title, artwork
-->

# MediaMetadata：JavaScript 中的媒體元數據管理

## 概要
MediaMetadata 是一個 Web API，允許開發者在網頁中提供媒體內容的元數據，從而改善用戶體驗，尤其是在播放音樂和影片時。它使網站能夠顯示歌曲標題、藝術家、專輯封面等信息。

## 文檔
### 目的
MediaMetadata 的主要目的是讓開發者能夠為正在播放的媒體提供豐富的元數據，這有助於用戶在多任務處理時獲取相關信息，例如在設備的鎖定螢幕上或通知列中。

### 使用方法
要使用 MediaMetadata，首先需要創建一個 MediaMetadata 的實例，並將元數據設置為一組屬性。這些屬性包括 `title`、`artist`、`album`、`artwork` 等。以下是基本的使用方式：

```javascript
if ('MediaMetadata' in window) {
    const metadata = new MediaMetadata({
        title: '歌曲標題',
        artist: '藝術家名稱',
        album: '專輯名稱',
        artwork: [
            { src: '封面圖片網址', sizes: '512x512', type: 'image/png' }
        ]
    });

    navigator.mediaSession.metadata = metadata;
}
```

### 詳細說明
- **屬性**：
  - `title` (String)：媒體的標題。
  - `artist` (String)：藝術家的名稱。
  - `album` (String)：專輯的名稱。
  - `artwork` (Array)：包含一個或多個物件，每個物件包含媒體封面的圖片網址、大小和類型。

- **相容性**：
  - 確保在使用之前檢查瀏覽器的相容性，因為某些舊版瀏覽器可能不支援此 API。

- **更新元數據**：
  - 可以在媒體播放時動態更新元數據，只需重新設置 `navigator.mediaSession.metadata` 即可。

## 範例
以下是一個簡單的範例，展示如何在播放音樂時設置和更新媒體元數據：

```javascript
if ('MediaMetadata' in window) {
    const metadata = new MediaMetadata({
        title: '新歌',
        artist: '新藝術家',
        album: '新專輯',
        artwork: [
            { src: 'https://example.com/artwork.jpg', sizes: '512x512', type: 'image/jpeg' }
        ]
    });

    navigator.mediaSession.metadata = metadata;

    // 更新元數據示範
    function updateMetadata(newTitle) {
        metadata.title = newTitle;
        navigator.mediaSession.metadata = metadata;
    }

    updateMetadata('更新後的歌曲標題');
}
```

## 解釋
### 常見陷阱
- **相容性問題**：在實作之前，請確保目標瀏覽器支援 MediaMetadata API。
- **藝術作品顯示問題**：確保圖片的網址正確且可訪問，否則藝術作品可能無法顯示。

### 附加說明
- 這個 API 對於音樂和影片應用特別有用，能在用戶的設備上提供良好的媒體體驗。
- 請注意，過度頻繁地更新元數據可能會影響性能，因此應謹慎使用。

## 一句總結
MediaMetadata 是一個強大的 API，幫助開發者為網頁媒體內容提供豐富的元數據，從而提升用戶體驗。