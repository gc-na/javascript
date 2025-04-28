<!--
Meta Description: # MediaStreamTrackVideoStats 在 JavaScript 中的使用指南 ## 概述 `MediaStreamTrackVideoStats` 是一個用於獲取和分析視頻流的統計信息的 JavaScript 介面。這個介面對於開發者在處理媒體流時，尤其是在WebRTC應用中，提...
Meta Keywords: mediastreamtrackvideostats, report, getstats, console, javascript
-->

# MediaStreamTrackVideoStats 在 JavaScript 中的使用指南

## 概述
`MediaStreamTrackVideoStats` 是一個用於獲取和分析視頻流的統計信息的 JavaScript 介面。這個介面對於開發者在處理媒體流時，尤其是在WebRTC應用中，提供了有用的性能數據。

## 文檔
`MediaStreamTrackVideoStats` 提供了一系列的屬性，讓開發者可以獲取有關視頻流的詳細統計信息。這些信息包括但不限於視頻的解析度、幀率、丟幀率和編碼器使用情況。這些數據對於優化視頻質量和用戶體驗至關重要。

### 用法
要使用 `MediaStreamTrackVideoStats`，你需要首先獲取一個 `MediaStreamTrack` 物件，然後透過 `getStats()` 方法來獲取統計數據。以下是基本的使用步驟：

1. 獲取媒體流，例如使用 `getUserMedia()`。
2. 獲取 `MediaStreamTrack` 物件，通常是視頻流的一部分。
3. 調用 `getStats()` 方法來獲取統計數據，然後尋找 `MediaStreamTrackVideoStats` 相關的數據。

### 主要屬性
- `width`: 當前視頻的寬度（像素）。
- `height`: 當前視頻的高度（像素）。
- `framesPerSecond`: 每秒幀數。
- `framesEncoded`: 已編碼的幀數。
- `framesDropped`: 丟失的幀數。

## 範例
以下是一個基本的使用範例，展示如何獲取和顯示 `MediaStreamTrackVideoStats` 數據：

```javascript
navigator.mediaDevices.getUserMedia({ video: true })
  .then(stream => {
    const videoTrack = stream.getVideoTracks()[0];
    const peerConnection = new RTCPeerConnection();

    peerConnection.addTrack(videoTrack);

    setInterval(() => {
      peerConnection.getStats(videoTrack).then(stats => {
        stats.forEach(report => {
          if (report.type === 'video') {
            console.log(`寬度: ${report.width}, 高度: ${report.height}`);
            console.log(`每秒幀數: ${report.framesPerSecond}`);
            console.log(`已編碼幀數: ${report.framesEncoded}`);
            console.log(`丟失幀數: ${report.framesDropped}`);
          }
        });
      });
    }, 1000);
  })
  .catch(error => {
    console.error('獲取媒體流失敗:', error);
  });
```

## 解釋
在使用 `MediaStreamTrackVideoStats` 時，開發者應注意以下幾點：

- **延遲性**：獲取統計數據可能會有延遲，因此不應依賴於即時數據。
- **瀏覽器兼容性**：並非所有瀏覽器都完全支持 `getStats()` 方法和其返回的所有統計數據，確保進行必要的兼容性檢查。
- **性能考量**：頻繁調用 `getStats()` 可能會影響性能，建議使用定時器來控制調用頻率。

## 一句總結
`MediaStreamTrackVideoStats` 是一個強大的工具，幫助開發者在 JavaScript 中獲取視頻流的性能統計信息。