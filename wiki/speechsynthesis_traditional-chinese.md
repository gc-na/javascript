<!--
Meta Description: # JavaScript 語音合成 (SpeechSynthesis) 功能詳解 ## 概述 JavaScript 的語音合成功能 (SpeechSynthesis) 允許開發者透過瀏覽器讓應用程序具備語音朗讀的能力。這項技術可用於提升無障礙性、增強用戶體驗，並在多種應用中廣泛使用，例如電子書、語音...
Meta Keywords: speechsynthesis, utterance, javascript, speak, speechsynthesisutterance
-->

# JavaScript 語音合成 (SpeechSynthesis) 功能詳解

## 概述
JavaScript 的語音合成功能 (SpeechSynthesis) 允許開發者透過瀏覽器讓應用程序具備語音朗讀的能力。這項技術可用於提升無障礙性、增強用戶體驗，並在多種應用中廣泛使用，例如電子書、語音助手等。

## 文件說明
### 目的
`SpeechSynthesis` 是 Web 語音 API 的一部分，旨在提供一個簡單的介面來生成語音輸出。這項功能允許開發者將文字轉換為自然語音，並且支持多種語言和聲音選擇。

### 使用方式
要使用 `SpeechSynthesis`，首先需要檢查瀏覽器是否支持該功能。以下是基本的使用步驟：

1. **檢查支持性**：
   ```javascript
   if ('speechSynthesis' in window) {
       console.log("這個瀏覽器支持語音合成！");
   } else {
       console.log("這個瀏覽器不支持語音合成。");
   }
   ```

2. **創建語音實例**：
   使用 `SpeechSynthesisUtterance` 對象來創建要朗讀的文字。
   ```javascript
   const utterance = new SpeechSynthesisUtterance("你好，歡迎使用語音合成！");
   ```

3. **選擇語音**：
   可以選擇不同的語音和設定語速、音調等屬性。
   ```javascript
   utterance.voice = speechSynthesis.getVoices()[0]; // 選擇第一個可用語音
   utterance.rate = 1; // 語速
   utterance.pitch = 1; // 音調
   ```

4. **開始朗讀**：
   最後，使用 `speechSynthesis.speak()` 方法開始朗讀。
   ```javascript
   speechSynthesis.speak(utterance);
   ```

### 詳細資訊
- **屬性**：
  - `voice`: 設定語音的樣式。
  - `rate`: 語速，範圍是 0.1 到 10，預設為 1。
  - `pitch`: 音調，範圍是 0 到 2，預設為 1。
  - `volume`: 音量，範圍是 0 到 1，預設為 1。

- **方法**：
  - `speak(utterance)`: 開始朗讀文字。
  - `cancel()`: 停止當前的朗讀。
  - `pause()`: 暫停朗讀。
  - `resume()`: 恢復暫停的朗讀。

- **事件**：
  - `onend`: 朗讀結束時觸發。
  - `onstart`: 朗讀開始時觸發。
  - `onerror`: 朗讀過程中發生錯誤時觸發。

## 範例
以下是一個簡單的範例，展示如何使用語音合成功能：
```javascript
const utterance = new SpeechSynthesisUtterance("這是一個語音合成的示例。");
utterance.voice = speechSynthesis.getVoices()[0];
speechSynthesis.speak(utterance);
```

## 解釋
在使用 `SpeechSynthesis` 時需注意以下幾點：
- 瀏覽器支持性：並非所有瀏覽器都支持語音合成，需確保在開發過程中進行檢查。
- 語音列表加載：語音列表可能需要時間加載，建議使用 `getVoices()` 方法後再設定語音。
- 事件處理：確保對語音的開始、結束及錯誤事件進行適當處理，以提升用戶體驗。

## 一句話總結
JavaScript 的語音合成 (SpeechSynthesis) 功能提供了一種簡單有效的方式，將文字轉換為自然語音，增強了應用的可及性和互動性。