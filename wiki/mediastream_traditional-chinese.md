<!--
Meta Description: # MediaStream：JavaScript中的媒體流處理 ## 概述 MediaStream 是一個 JavaScript API，用於處理音頻和視頻流，通常用於WebRTC、錄製和媒體傳輸。它允許開發者獲取和操作來自用戶設備（如麥克風和攝像頭）的媒體數據流。 ## 文檔 ### 目的 Med...
Meta Keywords: mediastream, video, track, getusermedia, javascript
-->

# MediaStream：JavaScript中的媒體流處理

## 概述
MediaStream 是一個 JavaScript API，用於處理音頻和視頻流，通常用於WebRTC、錄製和媒體傳輸。它允許開發者獲取和操作來自用戶設備（如麥克風和攝像頭）的媒體數據流。

## 文檔
### 目的
MediaStream 主要用來表示一組媒體通道，這些通道可以是音頻通道、視頻通道或兩者的組合。它是WebRTC應用程序的基石，允許在瀏覽器之間進行即時音視頻通訊。

### 使用
使用 MediaStream 的基本步驟如下：
1. **獲取媒體流**：通過 `navigator.mediaDevices.getUserMedia()` 方法獲取來自用戶的媒體流。
2. **操作媒體流**：可以將獲取的流傳遞給 `<video>` 或 `<audio>` 標籤，或者進行其他處理，如錄製。

### 詳細說明
- **屬性**：MediaStream 包含多個屬性，如 `active`（指示流是否處於活動狀態）和 `getTracks()`（獲取流中的所有媒體軌道）。
- **方法**：
  - `addTrack(track)`：向流中添加一個媒體軌道。
  - `removeTrack(track)`：從流中移除一個媒體軌道。
- **事件**：MediaStream 觸發的事件包括 `active` 和 `inactive`，用於表示流的狀態。

## 範例
### 獲取媒體流並顯示
```javascript
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
  .then(function(stream) {
    const video = document.querySelector('video');
    video.srcObject = stream;
    video.play();
  })
  .catch(function(err) {
    console.error("獲取媒體流失敗：", err);
  });
```

### 添加音頻軌道
```javascript
const mediaStream1 = await navigator.mediaDevices.getUserMedia({ audio: true });
const mediaStream2 = await navigator.mediaDevices.getUserMedia({ video: true });

const combinedStream = new MediaStream();
mediaStream1.getTracks().forEach(track => combinedStream.addTrack(track));
mediaStream2.getTracks().forEach(track => combinedStream.addTrack(track));
```

## 解釋
### 常見陷阱
- 確保用戶已授權使用攝像頭和麥克風，否則 `getUserMedia` 將失敗。
- 注意處理 `Promise`，以捕獲錯誤和異常情況。
- 媒體流的活躍狀態可能會受到用戶行為（如關閉攝像頭）的影響。

### 額外說明
- 認識到 MediaStream 對於即時通訊和多媒體應用的重要性，能幫助開發者更好地利用其功能。

## 一句話總結
MediaStream 是一個強大的 JavaScript API，用於處理來自用戶設備的音視頻流，並支持即時通訊和媒體操作。