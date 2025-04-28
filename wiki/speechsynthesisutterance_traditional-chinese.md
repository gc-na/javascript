<!--
Meta Description: # SpeechSynthesisUtterance：JavaScript 語音合成的強大工具 ## 簡介 `SpeechSynthesisUtterance` 是一個 JavaScript 介面，允許開發者在網頁中合成語音。它是 Web Speech API 的一部分，使得網頁可以將文字轉換為語音...
Meta Keywords: utterance, speechsynthesisutterance, javascript, speechsynthesis, lang
-->

# SpeechSynthesisUtterance：JavaScript 語音合成的強大工具

## 簡介
`SpeechSynthesisUtterance` 是一個 JavaScript 介面，允許開發者在網頁中合成語音。它是 Web Speech API 的一部分，使得網頁可以將文字轉換為語音，提升用戶互動體驗。

## 文檔
`SpeechSynthesisUtterance` 的主要目的是讓開發者能夠創建語音合成的實例。這些實例可以設定語音的內容、語速、音調及音量，並可以通過 `SpeechSynthesis` 對象進行播放。

### 使用方式
使用 `SpeechSynthesisUtterance` 的基本步驟如下：

1. **創建實例**：
   ```javascript
   const utterance = new SpeechSynthesisUtterance('你好，歡迎使用語音合成！');
   ```

2. **設定屬性**：
   ```javascript
   utterance.lang = 'zh-TW'; // 語言設置
   utterance.rate = 1; // 語速
   utterance.pitch = 1; // 音調
   utterance.volume = 1; // 音量
   ```

3. **播放語音**：
   ```javascript
   speechSynthesis.speak(utterance);
   ```

### 詳細說明
- **屬性**：
  - `text`：要合成的文字內容。
  - `lang`：語言代碼，決定語音的語言。
  - `rate`：語速，範圍通常在 0.1 到 10 之間，預設為 1。
  - `pitch`：音調，範圍通常在 0 到 2 之間，預設為 1。
  - `volume`：音量，範圍從 0 到 1，預設為 1。

- **方法**：
  - `cancel()`：取消所有正在播放的語音。
  - `pause()`：暫停語音播放。
  - `resume()`：恢復暫停的語音播放。

## 範例
以下是一些基本的使用範例：

### 範例 1：簡單的語音合成
```javascript
const utterance = new SpeechSynthesisUtterance('這是一個簡單的語音合成範例。');
speechSynthesis.speak(utterance);
```

### 範例 2：自定義語音屬性
```javascript
const utterance = new SpeechSynthesisUtterance('這是一個自定義語音的範例。');
utterance.lang = 'zh-TW';
utterance.rate = 1.5;
utterance.pitch = 1.2;
speechSynthesis.speak(utterance);
```

## 解釋
在使用 `SpeechSynthesisUtterance` 時，有一些常見的陷阱需要注意：

- **語音支持**：並非所有瀏覽器都支持所有語音，使用前需確認瀏覽器的語音合成功能。
- **語言設置**：確保 `lang` 屬性設置正確，否則語音合成可能無法正常運作。
- **使用頻率**：過於頻繁地調用 `speak()` 可能會導致語音播放不順暢。

## 一句總結
`SpeechSynthesisUtterance` 是一個強大的 JavaScript 介面，能夠輕鬆實現網頁中的語音合成功能。