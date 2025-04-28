<!--
Meta Description: # 離線音訊完成事件 (OfflineAudioCompletionEvent) 在 JavaScript 中的應用 ## 簡介 離線音訊完成事件（OfflineAudioCompletionEvent）是 Web Audio API 的一部分，專門用於處理離線音訊上下文中的音訊處理結果。這個事件在...
Meta Keywords: offlineaudiocontext, offlineaudiocompletionevent, offlinecontext, audiosource, then
-->

# 離線音訊完成事件 (OfflineAudioCompletionEvent) 在 JavaScript 中的應用

## 簡介
離線音訊完成事件（OfflineAudioCompletionEvent）是 Web Audio API 的一部分，專門用於處理離線音訊上下文中的音訊處理結果。這個事件在音訊處理完成後被觸發，讓開發者能夠獲取生成的音訊緩衝區。

## 文檔
### 目的
OfflineAudioCompletionEvent 的主要目的是在離線音訊處理完成時通知開發者，並提供生成的音訊緩衝區，以便進一步使用或播放。

### 使用方式
離線音訊完成事件通常與 OfflineAudioContext 一起使用。當使用 OfflineAudioContext 進行音訊處理時，開發者可以註冊對離線音訊完成事件的監聽器，並在事件發生時獲取音訊緩衝區。

### 詳細說明
- **事件屬性**：
  - `renderedBuffer`：這是一個 AudioBuffer 物件，包含處理後的音訊數據。
  
- **事件類型**：
  OfflineAudioCompletionEvent 是一個自定義事件，當 OfflineAudioContext 完成渲染音訊時觸發。

- **觸發方式**：
  當 OfflineAudioContext 的 `startRendering()` 方法被調用並且音訊渲染完成後，將觸發此事件。

## 範例
以下是使用 OfflineAudioCompletionEvent 的基本範例：

```javascript
// 創建 OfflineAudioContext
const offlineContext = new OfflineAudioContext(2, 44100 * 40, 44100);

// 創建音訊源
const audioSource = offlineContext.createBufferSource();

// 加載音訊緩衝區
fetch('your-audio-file.mp3')
    .then(response => response.arrayBuffer())
    .then(arrayBuffer => offlineContext.decodeAudioData(arrayBuffer))
    .then(audioBuffer => {
        audioSource.buffer = audioBuffer;
        audioSource.connect(offlineContext.destination);
        audioSource.start();

        // 開始渲染音訊
        offlineContext.startRendering().then(renderedBuffer => {
            console.log('渲染完成的音訊緩衝區:', renderedBuffer);
        }).catch(error => {
            console.error('渲染失敗:', error);
        });
    });
```

## 解釋
在使用 OfflineAudioCompletionEvent 時，開發者需要注意以下幾點：
- 確保在調用 `startRendering()` 之前，音訊源已經正確連接到 OfflineAudioContext 的目的地。
- 渲染過程可能會因為音訊數據不完整或格式不正確而失敗，因此需要妥善處理錯誤。
- 由於 OfflineAudioContext 在 Web Worker 中無法運行，因此需要在主執行緒中使用。

## 一句總結
OfflineAudioCompletionEvent 是一個用於處理離線音訊上下文中音訊渲染完成的事件，提供了生成的音訊緩衝區以供後續使用。