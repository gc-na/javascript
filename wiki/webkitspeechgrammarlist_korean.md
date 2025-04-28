<!--
Meta Description: # webkitSpeechGrammarList: 자바스크립트의 음성 인식 문법 관리 ## 개요 `webkitSpeechGrammarList`는 웹 음성 인식을 위한 문법 목록을 정의하고 관리하는 데 사용되는 JavaScript 인터페이스입니다. 이 인터페이스는 사용자 ...
Meta Keywords: webkitspeechgrammarlist, recognition, grammar, var, grammarlist
-->

# webkitSpeechGrammarList: 자바스크립트의 음성 인식 문법 관리

## 개요
`webkitSpeechGrammarList`는 웹 음성 인식을 위한 문법 목록을 정의하고 관리하는 데 사용되는 JavaScript 인터페이스입니다. 이 인터페이스는 사용자 음성 인식의 정확성을 높이기 위해 필요한 문법 패턴을 설정할 수 있게 해줍니다.

## 문서화
### 목적
`webkitSpeechGrammarList`는 웹 애플리케이션에서 음성 인식을 활용할 때, 특정 단어나 구문을 인식할 수 있도록 문법을 정의하는 역할을 합니다. 이는 특히 특정 단어나 구문을 인식해야 하는 애플리케이션에서 유용합니다.

### 사용법
`webkitSpeechGrammarList`는 `webkitSpeechRecognition` 객체의 `grammars` 속성으로 접근할 수 있습니다. 이 속성을 통해 새로운 문법을 추가하거나 수정할 수 있습니다.

#### 문법 생성
1. `webkitSpeechGrammarList` 객체를 생성합니다.
2. 문법을 추가합니다.
3. 음성 인식기 객체에 이 문법 목록을 할당합니다.

```javascript
var recognition = new webkitSpeechRecognition();
var grammarList = new webkitSpeechGrammarList();

// 문법 정의
var grammar = '#JSGF V1.0; grammar colors; public <color> = red | green | blue | yellow ;';
grammarList.addFromString(grammar, 1);

// 문법 목록을 recognition 객체에 할당
recognition.grammars = grammarList;
```

### 세부사항
- **지원 브라우저**: `webkitSpeechGrammarList`는 주로 WebKit 기반 브라우저에서 사용됩니다. 크롬과 사파리에서 지원되며, 최신 브라우저에서의 지원 여부를 확인해야 합니다.
- **문법 형식**: 문법은 JSGF(Java Speech Grammar Format) 형식으로 작성되어야 하며, 이 형식에 맞추어야 올바르게 작동합니다.
- **빈 문법 목록**: 문법 목록이 비어 있을 경우, 음성 인식은 모든 단어와 구문을 인식하도록 설정됩니다.

## 예제
### 기본 사용 예제
```javascript
var recognition = new webkitSpeechRecognition();
var grammarList = new webkitSpeechGrammarList();

var grammar = '#JSGF V1.0; grammar example; public <command> = start | stop ;';
grammarList.addFromString(grammar, 1);
recognition.grammars = grammarList;

recognition.onresult = function(event) {
  console.log('Recognized: ' + event.results[0][0].transcript);
};

recognition.start();
```

## 설명
### 일반적인 오류 및 주의 사항
- **브라우저 호환성**: `webkitSpeechGrammarList`는 모든 브라우저에서 지원되지 않으므로, 사용 전에 지원 여부를 확인해야 합니다.
- **정확성**: 문법이 포함되지 않은 단어나 구문은 인식되지 않을 수 있습니다. 따라서 필요한 모든 단어와 구문을 문법에 포함하는 것이 중요합니다.
- **JSGF 문법 오류**: JSGF 형식이 올바르지 않으면 문법이 무시될 수 있습니다. 문법을 철저히 검토해야 합니다.

## 한 줄 요약
`webkitSpeechGrammarList`는 웹 음성 인식에서 특정 단어나 구문을 정의하여 인식의 정확성을 높이는 JavaScript 인터페이스입니다.