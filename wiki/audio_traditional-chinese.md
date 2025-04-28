<!--
Meta Description: # JavaScript 中的音頻 (Audio) 操作指南 ## 概述 在 JavaScript 中，音頻處理是網頁應用程式的重要功能之一。使用 HTML5 的 `<audio>` 標籤以及 JavaScript 的 Web Audio API，開發者可以輕鬆地播放、控制和分析音頻。 ## 文檔 ...
Meta Keywords: audio, javascript, const, oscillator, web
-->

# JavaScript 中的音頻 (Audio) 操作指南

## 概述
在 JavaScript 中，音頻處理是網頁應用程式的重要功能之一。使用 HTML5 的 `<audio>` 標籤以及 JavaScript 的 Web Audio API，開發者可以輕鬆地播放、控制和分析音頻。

## 文檔
### 目的
JavaScript 提供了多種方法來處理音頻內容，使得網頁能夠播放音樂、效果聲和其他音頻資料，增強用戶體驗。

### 使用方法
1. **使用 HTML `<audio>` 標籤**：
   ```html
   <audio id="myAudio" controls>
       <source src="audio-file.mp3" type="audio/mpeg">
       您的瀏覽器不支持音頻元素。
   </audio>
   ```

2. **使用 JavaScript 操作音頻**：
   ```javascript
   const audio = document.getElementById('myAudio');

   // 播放音頻
   audio.play();

   // 暫停音頻
   audio.pause();

   // 調整音量
   audio.volume = 0.5; // 介於 0.0 和 1.0 之間的值
   ```

3. **利用 Web Audio API**：
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   const audioElement = document.getElementById('myAudio');
   const track = audioContext.createMediaElementSource(audioElement);
   track.connect(audioContext.destination);
   ```

### 詳細說明
- **HTML `<audio>` 標籤**：提供基本的音頻播放功能，支持多種音頻格式（如 MP3、WAV、OGG）。
- **JavaScript 控制**：通過 DOM 操作，可以控制音頻的播放、暫停、音量和播放進度。
- **Web Audio API**：提供更高層次的音頻處理能力，包括音效處理、音頻分析等。

## 範例
### 基本用法
```html
<audio id="myAudio" controls>
    <source src="sound.mp3" type="audio/mpeg">
    您的瀏覽器不支持音頻元素。
</audio>

<script>
    const audio = document.getElementById('myAudio');
    audio.play(); // 播放音頻
</script>
```

### Web Audio API 範例
```javascript
const context = new (window.AudioContext || window.webkitAudioContext)();
const oscillator = context.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, context.currentTime); // A4
oscillator.connect(context.destination);
oscillator.start();
oscillator.stop(context.currentTime + 1); // 播放 1 秒
```

## 說明
- **常見陷阱**：
  - 瀏覽器自動播放限制：許多瀏覽器禁止自動播放音頻，必須在用戶交互後才可播放。
  - 音頻格式支持：不同瀏覽器對音頻格式的支持有所不同，建議提供多種格式以保證兼容性。

## 一句總結
JavaScript 提供了強大的音頻處理功能，通過 HTML 和 Web Audio API 使音頻控制變得簡單易用。