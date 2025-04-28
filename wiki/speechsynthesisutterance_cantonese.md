<!--
Meta Description: # SpeechSynthesisUtterance：JavaScript 語音合成的強大工具 ## 簡介 `SpeechSynthesisUtterance` 是一個 JavaScript 物件，專門用於創建和控制語音合成的內容，讓開發者能夠在網頁或應用程式中添加語音功能。 ## 文檔 `Spee...
Meta Keywords: speechsynthesisutterance, utterance, javascript, new, text
-->

# SpeechSynthesisUtterance：JavaScript 語音合成的強大工具

## 簡介
`SpeechSynthesisUtterance` 是一個 JavaScript 物件，專門用於創建和控制語音合成的內容，讓開發者能夠在網頁或應用程式中添加語音功能。

## 文檔
`SpeechSynthesisUtterance` 是 Web 語音 API 的一部分，允許用戶將文本轉換為語音。透過這個物件，開發者可以設置語音的內容、說話的語速、音調及語言等屬性。其主要目的是提高可訪問性，使得文字內容能夠更易於被聽眾理解。

### 用法
要使用 `SpeechSynthesisUtterance`，首先需要創建一個新的實例，然後設置其屬性，最後將其加入到語音合成的佇列中。以下是基本步驟：

1. **創建實例**：使用 `new SpeechSynthesisUtterance(text)` 來創建一個新的實例，其中 `text` 是要合成的文本。
2. **設置屬性**：可以設置如 `lang`, `pitch`, `rate`, `volume` 等屬性。
3. **語音合成**：使用 `speechSynthesis.speak(utterance)` 方法來開始語音合成。

## 範例
以下是使用 `SpeechSynthesisUtterance` 的基本範例：

```javascript
// 創建一個新的語音合成實例
let utterance = new SpeechSynthesisUtterance("你好，歡迎使用語音合成！");

// 設置語言
utterance.lang = 'zh-HK';

// 設置語速
utterance.rate = 1;

// 語音合成
window.speechSynthesis.speak(utterance);
```

## 解釋
在使用 `SpeechSynthesisUtterance` 時，開發者需注意以下幾點：

- **瀏覽器支持**：並非所有瀏覽器都對語音合成提供相同的支持。建議在使用前檢查瀏覽器的兼容性。
- **語音選擇**：不同的系統和瀏覽器可能提供不同的語音選擇，這可能會影響最終的語音效果。
- **異步行為**：語音合成是一個異步過程，開發者應考慮如何處理合成過程中的狀態變化，例如完成、錯誤等事件。

## 一句總結
`SpeechSynthesisUtterance` 是一個強大的 JavaScript 工具，可用於將文本轉換為語音，增強網頁的可訪問性和互動性。