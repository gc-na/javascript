<!--
Meta Description: # webkitSpeechGrammarList：在 JavaScript 中的語音識別文法列表 ## 概述 `webkitSpeechGrammarList` 是 Web 語音 API 的一部分，允許開發者為語音識別提供自訂文法。這種文法可幫助提高語音識別的準確性，特別是在特定上下文或應用中。 ...
Meta Keywords: webkitspeechgrammarlist, recognition, var, api, grammarlist
-->

# webkitSpeechGrammarList：在 JavaScript 中的語音識別文法列表

## 概述
`webkitSpeechGrammarList` 是 Web 語音 API 的一部分，允許開發者為語音識別提供自訂文法。這種文法可幫助提高語音識別的準確性，特別是在特定上下文或應用中。

## 文檔
### 目的
`webkitSpeechGrammarList` 主要用於支持語音識別的應用程序，開發者可以定義一組可接受的語音輸入，從而提高識別的準確性和效率。

### 使用方法
要使用 `webkitSpeechGrammarList`，首先需要訪問 `SpeechRecognition` 的實例，然後創建一個文法列表，將其設置到語音識別實例中。以下是基本步驟：

1. 創建 `SpeechRecognition` 實例。
2. 創建 `webkitSpeechGrammarList` 的實例。
3. 添加自定義文法。
4. 將文法列表設置為語音識別的文法。

### 詳細信息
- `webkitSpeechGrammarList` 是一個可讀寫的對象，可以添加多個文法。
- 文法通常以 BNF（巴克斯-諾爾范式）格式定義。
- 此 API 目前主要在 Chrome 瀏覽器中得到支持。

## 範例
以下是使用 `webkitSpeechGrammarList` 的基本示例：

```javascript
// 創建語音識別實例
var recognition = new webkitSpeechRecognition();

// 創建文法列表
var grammarList = new webkitSpeechGrammarList();

// 定義文法，使用 BNF 格式
var grammar = '#JSGF V1.0; grammar colors; public <color> = red | green | blue ;';

// 將文法添加到文法列表
grammarList.addFromString(grammar, 1);

// 設置語音識別的文法
recognition.grammars = grammarList;

// 當語音識別啟動時
recognition.onstart = function() {
  console.log('語音識別已啟動');
};

// 當語音識別結果返回時
recognition.onresult = function(event) {
  var transcript = event.results[0][0].transcript;
  console.log('識別結果：', transcript);
};

// 開始語音識別
recognition.start();
```

## 解釋
在使用 `webkitSpeechGrammarList` 時，開發者可能會遇到以下幾個常見問題：

1. **瀏覽器兼容性**：`webkitSpeechGrammarList` 目前主要在 Chrome 瀏覽器有效，其他瀏覽器可能不支持此 API。
2. **文法格式**：文法必須正確編寫，否則會導致語音識別失敗。
3. **限制和性能影響**：過多的文法可能影響語音識別的性能，建議根據實際需要精簡文法。

## 總結
`webkitSpeechGrammarList` 是一個強大的工具，能夠幫助開發者為語音識別提供高效的自訂文法，提高識別準確性。