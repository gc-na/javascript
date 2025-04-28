<!--
Meta Description: # SpeechSynthesisVoice：JavaScript 語音合成的關鍵組件 ## 摘要 `SpeechSynthesisVoice` 是 Web Speech API 的一部分，允許開發者使用不同的語音合成選項來生成語音，增強應用程式的可訪問性和互動性。 ## 文件說明 `SpeechS...
Meta Keywords: speechsynthesisvoice, voice, javascript, speechsynthesis, voices
-->

# SpeechSynthesisVoice：JavaScript 語音合成的關鍵組件

## 摘要
`SpeechSynthesisVoice` 是 Web Speech API 的一部分，允許開發者使用不同的語音合成選項來生成語音，增強應用程式的可訪問性和互動性。

## 文件說明
`SpeechSynthesisVoice` 是一個表示可用語音的物件，提供了有關語音合成的各種屬性和方法。開發者可以使用此物件來選擇和配置語音合成，包括語音的名稱、語言、性別和其他特徵。這使得開發者能夠提供多樣化的語音選擇，以適應不同用戶的需求。

### 目的
`SpeechSynthesisVoice` 的主要目的是提供一個接口，用於獲取可用的語音選項，讓開發者能夠根據應用的需求選擇合適的語音。

### 使用方法
要使用 `SpeechSynthesisVoice`，需要先獲取 `speechSynthesis` 物件，然後通過 `getVoices()` 方法來獲得語音列表。這個列表會返回一個 `SpeechSynthesisVoice` 的陣列，開發者可以根據屬性來選擇合適的語音。

### 屬性
- **name**：語音的名稱。
- **lang**：語音的語言代碼。
- **localService**：布林值，指示語音是否為本地服務。
- **default**：布林值，指示語音是否為預設語音。

## 示例
以下是一些基本的使用示例，展示如何獲取和使用 `SpeechSynthesisVoice`。

### 獲取可用語音
```javascript
let voices = speechSynthesis.getVoices();
voices.forEach(voice => {
    console.log(`${voice.name} (${voice.lang})`);
});
```

### 設定語音並合成語音
```javascript
const utterance = new SpeechSynthesisUtterance('你好，歡迎使用語音合成。');
const voices = speechSynthesis.getVoices();
const selectedVoice = voices.find(voice => voice.name === 'Google 國語');

if (selectedVoice) {
    utterance.voice = selectedVoice;
}
speechSynthesis.speak(utterance);
```

## 解釋
在使用 `SpeechSynthesisVoice` 時，開發者需要注意以下幾點：
- 語音列表可能在頁面載入時尚未完全加載，應使用 `onvoiceschanged` 事件來監聽語音的加載事件。
- 某些瀏覽器可能僅支持特定的語音，開發者應在選擇語音前檢查可用性。
- 在不同的操作系統和瀏覽器中，語音的名稱和語言可能會有所不同，因此應提供備選方案。

## 一行總結
`SpeechSynthesisVoice` 是一個用於獲取和管理可用語音的物件，提升 JavaScript 應用中的語音合成功能。