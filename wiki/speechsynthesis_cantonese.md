<!--
Meta Description: # SpeechSynthesis 在 JavaScript 中的應用 ## 簡介 SpeechSynthesis 是一個 JavaScript API，允許開發者在網頁中生成語音，從而實現文字轉語音功能。這個 API 特別適合用於輔助技術、語音導航及遊戲等應用。 ## 文檔 ### 目的 Spee...
Meta Keywords: speechsynthesis, utterance, javascript, speak, api
-->

# SpeechSynthesis 在 JavaScript 中的應用

## 簡介
SpeechSynthesis 是一個 JavaScript API，允許開發者在網頁中生成語音，從而實現文字轉語音功能。這個 API 特別適合用於輔助技術、語音導航及遊戲等應用。

## 文檔
### 目的
SpeechSynthesis 提供了一個簡單的接口來進行語音合成，使用者可以透過 JavaScript 操控語音的生成。這使得開發者能夠將文字轉換為自然的語音，提升用戶體驗。

### 使用
要使用 SpeechSynthesis，首先需要獲取 `window.speechSynthesis` 對象。然後，通過創建 `SpeechSynthesisUtterance` 對象來設置要朗讀的文字及其屬性，如語速、音調和音量。

```javascript
const utterance = new SpeechSynthesisUtterance('你好，歡迎使用語音合成！');
window.speechSynthesis.speak(utterance);
```

### 詳細信息
- **屬性**：
  - `text`：要朗讀的文本內容。
  - `lang`：語音的語言（例如：'zh-HK' 表示香港中文）。
  - `rate`：語音的速度，範圍在 0.1 到 10 之間，預設為 1。
  - `pitch`：語音的音調，範圍在 0 到 2 之間，預設為 1。
  - `volume`：語音的音量，範圍在 0 到 1 之間，預設為 1。

- **方法**：
  - `speak(utterance)`：開始朗讀。
  - `cancel()`：停止所有語音。
  - `pause()`：暫停當前語音。
  - `resume()`：恢復暫停的語音。

## 示例
### 基本使用範例
```javascript
const utterance = new SpeechSynthesisUtterance('這是一個基本的語音合成範例。');
utterance.lang = 'zh-HK';
window.speechSynthesis.speak(utterance);
```

### 設定語速和音調
```javascript
const utterance = new SpeechSynthesisUtterance('調整語速和音調的範例。');
utterance.rate = 1.5; // 語速
utterance.pitch = 1.2; // 音調
window.speechSynthesis.speak(utterance);
```

## 解釋
### 常見問題
1. **語音不播放**：確保瀏覽器支持 SpeechSynthesis API，並且沒有靜音或被阻止的情況。
2. **語言不正確**：確認 `lang` 屬性設置為正確的語言代碼，並且所選語音支持該語言。
3. **性能問題**：在頻繁調用 `speak()` 方法時，可能會導致性能下降，建議使用 `pause()` 和 `resume()` 方法來控制語音播放。

## 總結
SpeechSynthesis 是一個強大的 JavaScript API，能夠輕鬆實現文字轉語音功能，提升網頁的互動性和可訪問性。