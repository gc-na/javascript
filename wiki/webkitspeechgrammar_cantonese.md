<!--
Meta Description: # webkitSpeechGrammar：JavaScript 語音識別的文法設定 ## 簡介 `webkitSpeechGrammar` 是一個用於 JavaScript 的屬性，主要用於定義語音識別的文法規則，讓開發者能夠更準確地解析用戶的語音輸入。 ## 文檔 ### 目的 `webkitS...
Meta Keywords: webkitspeechgrammar, recognition, javascript, grammars, grammar
-->

# webkitSpeechGrammar：JavaScript 語音識別的文法設定

## 簡介
`webkitSpeechGrammar` 是一個用於 JavaScript 的屬性，主要用於定義語音識別的文法規則，讓開發者能夠更準確地解析用戶的語音輸入。

## 文檔
### 目的
`webkitSpeechGrammar` 用於指定語音識別的文法，協助用戶在使用語音輸入時提高識別的準確性。這一屬性通常與 WebKit 語音識別 API 一起使用，支持語音控制和語音轉文本功能。

### 用法
要使用 `webkitSpeechGrammar`，首先需要創建一個 `webkitSpeechRecognition` 的實例，然後將文法規則傳遞給該實例的 `grammars` 屬性。文法規則以特定格式指定，並且可以包含多個規則。

### 詳細信息
- **屬性類型**：`webkitSpeechGrammar` 是一個字串，包含文法規則的描述。
- **支援瀏覽器**：主要支援基於 WebKit 的瀏覽器，如 Chrome 和 Safari。
- **有效文法格式**：文法需要遵循 BNF（巴克斯-諾爾形式）或類似的格式。

## 範例
### 基本用法
```javascript
// 創建語音識別實例
var recognition = new webkitSpeechRecognition();

// 定義文法
var grammar = '#JSGF V1.0; grammar phrase; public <phrase> = hello | goodbye;';

// 將文法加到語音識別中
recognition.grammars = new webkitSpeechGrammarList();
recognition.grammars.addFromString(grammar, 1);

// 開始語音識別
recognition.start();

// 處理識別結果
recognition.onresult = function(event) {
    console.log('識別結果:', event.results[0][0].transcript);
};
```

## 解釋
- **常見問題**：使用 `webkitSpeechGrammar` 時，開發者可能會遇到語音識別無法識別特定短語的情況。這通常是因為文法定義不正確或未包含用戶想要的詞彙。
- **注意事項**：確保文法格式正確，並且在添加文法後及時啟動語音識別。此外，語音識別功能可能會受到環境噪音的影響，因此建議在安靜的環境中進行測試。

## 一行總結
`webkitSpeechGrammar` 是 JavaScript 中用於指定語音識別的文法規則的屬性，提升語音輸入的準確性。