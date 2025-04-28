<!--
Meta Description: # AudioListener：JavaScript 中的音頻監聽器 ## 概述 `AudioListener` 是 Web Audio API 中的一個重要組件，負責接收來自音源的音頻數據並進行處理，特別是在3D音頻環境中，能夠模擬人耳的聽覺特性。 ## 文檔 ### 目的 `AudioListe...
Meta Keywords: audiolistener, audiocontext, web, audio, api
-->

# AudioListener：JavaScript 中的音頻監聽器

## 概述
`AudioListener` 是 Web Audio API 中的一個重要組件，負責接收來自音源的音頻數據並進行處理，特別是在3D音頻環境中，能夠模擬人耳的聽覺特性。

## 文檔
### 目的
`AudioListener` 的主要目的是在 Web 應用程式中提供一個音頻接收器，使開發者能夠控制聲音的方向、距離和其他音質特性。它是創建沉浸式音頻體驗的關鍵。

### 用法
要使用 `AudioListener`，首先需要創建一個 `AudioContext`，然後將 `AudioListener` 附加到該上下文中。以下是基本的使用步驟：

1. 創建一個 `AudioContext`。
2. 創建一個 `AudioListener` 的實例。
3. 將 `AudioListener` 附加到 `AudioContext`。
4. 使用音源和效果器進行音頻處理。

### 詳細信息
- `AudioListener` 提供了一些方法和屬性來控制音頻，例如位置、朝向和速度。
- 通常用於實現3D音頻效果，使聲音根據用戶的位置和方向進行變化。
- 在使用 `AudioListener` 時，必須在瀏覽器支持 Web Audio API 的環境中運行。

## 示例
以下是一個簡單的例子，展示如何使用 `AudioListener`：

```javascript
// 創建音頻上下文
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建音頻監聽器
const listener = audioContext.listener;

// 設置監聽器的位置
listener.setPosition(0, 0, 0);
listener.setOrientation(0, 0, -1, 0, 1, 0);

// 創建音源
const source = audioContext.createBufferSource();
// 加載音頻數據（假設已經加載到 buffer 中）
source.buffer = audioBuffer;

// 將音源連接到音頻上下文
source.connect(audioContext.destination);

// 播放音源
source.start(0);
```

## 解釋
使用 `AudioListener` 時，開發者應注意以下幾點：
- 確保音頻上下文在用戶互動後創建，因為某些瀏覽器會阻止自動播放。
- `setPosition` 和 `setOrientation` 方法需要根據實際需要進行設置，以確保音頻效果的正確性。
- 在不支持 Web Audio API 的環境中，使用時可能會出現問題，應進行相應的兼容性處理。

## 一句總結
`AudioListener` 是 Web Audio API 的核心組件，旨在提供3D音頻體驗，允許開發者控制音頻源的方向和距離。