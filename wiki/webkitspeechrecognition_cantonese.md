<!--
Meta Description: # webkitSpeechRecognition：JavaScript 語音識別 API 的詳細指南 ## 概述 `webkitSpeechRecognition` 是一個基於網頁的語音識別 API，允許開發者在網頁應用中集成語音識別功能。透過此 API，使用者可以使用語音輸入取代傳統的鍵盤輸入，...
Meta Keywords: recognition, webkitspeechrecognition, javascript, event, transcript
-->

# webkitSpeechRecognition：JavaScript 語音識別 API 的詳細指南

## 概述
`webkitSpeechRecognition` 是一個基於網頁的語音識別 API，允許開發者在網頁應用中集成語音識別功能。透過此 API，使用者可以使用語音輸入取代傳統的鍵盤輸入，增強互動性及可用性。

## 文檔
### 目的
`webkitSpeechRecognition` 的主要目的是提供一種簡便的方法來將語音轉換為文本，適用於多種應用場景，例如語音助手、語音搜尋或語音備忘錄等。

### 使用方法
要使用 `webkitSpeechRecognition`，需要進行以下步驟：

1. **創建實例**：
   ```javascript
   const recognition = new webkitSpeechRecognition();
   ```

2. **設置屬性**：
   設定語言及其他屬性，例如：
   ```javascript
   recognition.lang = 'zh-HK'; // 設定為廣東話
   recognition.interimResults = true; // 是否獲取中間結果
   ```

3. **定義事件處理器**：
   使用 `onresult` 事件來處理識別結果：
   ```javascript
   recognition.onresult = (event) => {
       const transcript = event.results[0][0].transcript;
       console.log(transcript);
   };
   ```

4. **啟動識別**：
   調用 `start()` 方法開始語音識別：
   ```javascript
   recognition.start();
   ```

### 詳細說明
`webkitSpeechRecognition` 提供了多個重要的屬性和方法：

- **屬性**：
  - `lang`：設置語言，範例：`'zh-HK'`。
  - `interimResults`：如果設為 `true`，將返回中間結果。
  - `maxAlternatives`：設置返回的最佳結果數量。

- **方法**：
  - `start()`：啟動語音識別。
  - `stop()`：停止語音識別。
  - `abort()`：中止語音識別過程。

- **事件**：
  - `onstart`：當識別開始時觸發。
  - `onend`：當識別結束時觸發。
  - `onerror`：當識別過程中出錯時觸發。

## 示例
以下是一些基本的使用範例：

### 例子 1：簡單的語音識別
```javascript
const recognition = new webkitSpeechRecognition();
recognition.lang = 'zh-HK';

recognition.onresult = (event) => {
    const transcript = event.results[0][0].transcript;
    console.log("識別結果：" + transcript);
};

recognition.start();
```

### 例子 2：處理錯誤
```javascript
recognition.onerror = (event) => {
    console.error("識別錯誤：" + event.error);
};

recognition.start();
```

## 解釋
使用 `webkitSpeechRecognition` 時需注意以下幾點：

1. **瀏覽器支持**：此 API 目前主要在 Chrome 瀏覽器中受到支持，其他瀏覽器可能不完全相容。
2. **麥克風權限**：用戶需授予麥克風的使用權限，否則識別將無法正常工作。
3. **語音質量**：環境噪音會影響語音識別的準確性，建議在安靜的環境中使用。

## 一句總結
`webkitSpeechRecognition` 是一個強大的 API，讓開發者能夠輕鬆地在網頁應用中實現語音識別功能。