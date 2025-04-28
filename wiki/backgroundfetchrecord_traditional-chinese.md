<!--
Meta Description: # BackgroundFetchRecord：JavaScript 背景取回記錄的全面介紹 ## 概述 **BackgroundFetchRecord** 是一個 JavaScript API，允許開發者在背景中管理和追蹤大型檔案的下載或上傳操作，特別適合在網路連線不穩定或需要持續更新的應用程式中...
Meta Keywords: backgroundfetchrecord, api, javascript, service, fetchrecord
-->

# BackgroundFetchRecord：JavaScript 背景取回記錄的全面介紹

## 概述
**BackgroundFetchRecord** 是一個 JavaScript API，允許開發者在背景中管理和追蹤大型檔案的下載或上傳操作，特別適合在網路連線不穩定或需要持續更新的應用程式中使用。

## 文檔
### 目的
BackgroundFetchRecord 提供了一種方式，使開發者能夠在網頁後台執行檔案的下載或上傳，並在下載過程中持續追蹤進度和狀態。

### 使用方法
要使用 BackgroundFetchRecord，開發者首先需要創建一個 BackgroundFetch 物件，然後可以使用該物件來管理 BackgroundFetchRecord。這個 API 主要支援在 Service Workers 中使用。

#### 屬性
- **id**: 唯一標識符，表示該記錄的 ID。
- **uploadTotal**: 上傳資料的總大小（以位元組為單位）。
- **uploading**: 當前上傳的資料大小。

#### 方法
- **abort()**: 中止當前的下載或上傳操作。
- **pause()**: 暫停當前的下載或上傳操作。
- **resume()**: 恢復之前暫停的操作。

## 範例
### 基本用法範例
```javascript
async function startBackgroundFetch() {
    const registration = await navigator.serviceWorker.ready;
    const fetchRecord = await registration.backgroundFetch.fetch('my-fetch', ['/large-file.zip'], {
        title: '大檔案下載',
        icons: [{ src: 'icon.png', sizes: '192x192', type: 'image/png' }],
        downloadTotal: 5000000 // 5MB
    });

    fetchRecord.addEventListener('progress', () => {
        console.log(`已下載: ${fetchRecord.uploading} / ${fetchRecord.uploadTotal}`);
    });
}
```

## 解釋
### 常見問題
- **支援狀態**: 確保在使用 BackgroundFetchRecord 之前，檢查瀏覽器是否支援 BackgroundFetch API。
- **Service Worker 需求**: 此 API 只能在 Service Worker 環境中使用，確保正確註冊 Service Worker。
- **網路連接**: 在不穩定的網路環境中，背景取回可能會暫停或中止，開發者應考慮到這一點並相應處理。

## 一句話總結
BackgroundFetchRecord 是一個強大的 JavaScript API，專為在背景中管理大型檔案的下載和上傳而設計，能有效提升用戶體驗。