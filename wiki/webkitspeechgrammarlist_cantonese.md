<!--
Meta Description: # webkitSpeechGrammarList：JavaScript 語音識別的語法列表 ## 概述 `webkitSpeechGrammarList` 是一個用於 JavaScript 的接口，屬於 Web 語音 API，用於定義語音識別的語法規則。透過此接口，開發者可以創建一組語法，指導語音...
Meta Keywords: webkitspeechgrammarlist, recognition, webkitspeechrecognition, javascript, grammar
-->

# webkitSpeechGrammarList：JavaScript 語音識別的語法列表

## 概述
`webkitSpeechGrammarList` 是一個用於 JavaScript 的接口，屬於 Web 語音 API，用於定義語音識別的語法規則。透過此接口，開發者可以創建一組語法，指導語音識別系統理解特定的語音輸入。

## 文檔
`webkitSpeechGrammarList` 的主要目的是提供一個可擴展的語法列表，來增強語音識別的準確性。它允許開發者將語法規則以字符串的形式添加到語音識別中，從而提升識別特定詞彙或短語的能力。

### 用法
要使用 `webkitSpeechGrammarList`，首先需要檢查用戶的瀏覽器是否支持語音識別。接著，可以創建一個 `webkitSpeechRecognition` 對象並設置其 `grammars` 屬性為一個新的 `webkitSpeechGrammarList` 實例。

### 詳細步驟：
1. 創建一個 `webkitSpeechRecognition` 實例。
2. 創建一個 `webkitSpeechGrammarList` 實例。
3. 使用 `addFromString` 方法將語法添加到語法列表中。
4. 將語法列表賦予 `webkitSpeechRecognition` 實例的 `grammars` 屬性。
5. 啟動語音識別。

## 示例
以下是一個基本的使用示例：

```javascript
// 檢查瀏覽器是否支持語音識別
if ('webkitSpeechRecognition' in window) {
    var recognition = new webkitSpeechRecognition();
    var grammarList = new webkitSpeechGrammarList();

    // 定義語法
    var grammar = '#JSGF V1.0; grammar colors; public <color> = red | green | blue ;';
    grammarList.addFromString(grammar, 1); // 添加語法到列表

    recognition.grammars = grammarList; // 設置語法列表
    recognition.continuous = false; // 不持續識別
    recognition.interimResults = false; // 不返回中間結果

    recognition.onresult = function(event) {
        console.log('你說的是：' + event.results[0][0].transcript);
    };

    recognition.start(); // 開始語音識別
} else {
    console.log('抱歉，您的瀏覽器不支持語音識別功能。');
}
```

## 解釋
在使用 `webkitSpeechGrammarList` 時，開發者應注意以下幾點：

- **瀏覽器兼容性**：`webkitSpeechGrammarList` 目前只在某些基於 WebKit 的瀏覽器中可用，例如 Chrome。因此，開發者應在使用之前檢查兼容性。
- **語法格式**：語法必須遵循 JSGF（Java Speech Grammar Format）格式，否則將無法正確解析。
- **性能考量**：添加過多的語法可能會影響語音識別的性能，建議根據實際需求合理設定。

## 一句總結
`webkitSpeechGrammarList` 是 JavaScript 中一個強大的工具，能夠通過自定義語法提升語音識別的準確性和靈活性。