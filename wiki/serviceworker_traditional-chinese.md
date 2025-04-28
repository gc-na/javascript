<!--
Meta Description: # ServiceWorker：JavaScript 中的服務工作者技術 ## 概述 ServiceWorker 是一種在網頁應用程式中運行的腳本，能夠在背景中處理網絡請求，使得應用程式能夠離線運行以及實現更快的加載速度。它是 Progressive Web Apps (PWA) 的核心組成部分。 ...
Meta Keywords: serviceworker, event, self, addeventlistener, javascript
-->

# ServiceWorker：JavaScript 中的服務工作者技術

## 概述
ServiceWorker 是一種在網頁應用程式中運行的腳本，能夠在背景中處理網絡請求，使得應用程式能夠離線運行以及實現更快的加載速度。它是 Progressive Web Apps (PWA) 的核心組成部分。

## 文檔
### 目的
ServiceWorker 的主要目的是提供一種方式，允許開發者攔截網絡請求，並根據需要提供自定義的響應。這使得應用程式可以在離線狀態下繼續工作，並且能有效地緩存資源，減少網絡延遲。

### 使用方式
1. **註冊 ServiceWorker**：
   使用 `navigator.serviceWorker.register()` 方法來註冊一個 ServiceWorker。註冊的文件應位於網站的根目錄或子目錄中，以確保能夠有效攔截該範圍內的所有請求。

   ```javascript
   if ('serviceWorker' in navigator) {
       navigator.serviceWorker.register('/service-worker.js')
           .then(registration => {
               console.log('ServiceWorker registration successful with scope: ', registration.scope);
           })
           .catch(error => {
               console.log('ServiceWorker registration failed: ', error);
           });
   }
   ```

2. **安裝和激活**：
   在 ServiceWorker 文件中，使用 `self.addEventListener` 來定義 `install` 和 `activate` 事件，這樣可以在安裝時緩存資源，並在激活時清理舊的快取。

   ```javascript
   self.addEventListener('install', event => {
       event.waitUntil(
           caches.open('my-cache').then(cache => {
               return cache.addAll([
                   '/',
                   '/index.html',
                   '/styles.css',
                   '/script.js'
               ]);
           })
       );
   });

   self.addEventListener('activate', event => {
       // 清理舊快取的邏輯
   });
   ```

3. **攔截網絡請求**：
   使用 `fetch` 事件來攔截請求，並提供相應的快取或網絡響應。

   ```javascript
   self.addEventListener('fetch', event => {
       event.respondWith(
           caches.match(event.request).then(response => {
               return response || fetch(event.request);
           })
       );
   });
   ```

### 詳細信息
- ServiceWorker 是一個異步的 API，需使用 Promise 進行操作。
- 只有在 HTTPS 環境或 localhost 下才能註冊 ServiceWorker。
- ServiceWorker 不會阻止網頁的加載，但能夠提供更高效的資源管理。

## 範例
以下是一個簡單的 ServiceWorker 實現範例，展示了如何緩存資源並處理網絡請求：

```javascript
// service-worker.js
self.addEventListener('install', event => {
    event.waitUntil(
        caches.open('v1').then(cache => {
            return cache.addAll([
                '/',
                '/index.html',
                '/styles.css',
                '/script.js'
            ]);
        })
    );
});

self.addEventListener('fetch', event => {
    event.respondWith(
        caches.match(event.request).then(response => {
            return response || fetch(event.request);
        })
    );
});
```

## 解釋
- **常見問題**：開發者在使用 ServiceWorker 時，可能會遇到快取過期或舊版本的問題，需定期清理快取。
- **注意事項**：ServiceWorker 運行於獨立的線程中，無法直接訪問 DOM，因此需要使用 postMessage 進行通信。
- **Debugging**：使用 Chrome 開發者工具的 Application 面板可以方便地查看和管理 ServiceWorker 和快取。

## 一句話總結
ServiceWorker 是一種強大的技術，可以使網頁應用程式在離線狀態下運行，並顯著提升性能和用戶體驗。