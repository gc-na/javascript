<!--
Meta Description: # SpeechSynthesisUtterance: 자바스크립트에서의 음성 합성 객체 ## 개요 `SpeechSynthesisUtterance`는 웹 브라우저에서 음성을 생성하여 텍스트를 읽어주는 데 사용되는 JavaScript 객체입니다. 이 객체는 Web Speech...
Meta Keywords: speechsynthesisutterance, utterance, 텍스트를, 음성의, 있습니다
-->

# SpeechSynthesisUtterance: 자바스크립트에서의 음성 합성 객체

## 개요
`SpeechSynthesisUtterance`는 웹 브라우저에서 음성을 생성하여 텍스트를 읽어주는 데 사용되는 JavaScript 객체입니다. 이 객체는 Web Speech API의 일부로, 사용자가 입력한 텍스트를 음성으로 변환할 수 있게 해줍니다.

## 문서화
### 목적
`SpeechSynthesisUtterance`의 주요 목적은 텍스트를 음성으로 변환하여 사용자에게 읽어주는 기능을 제공하는 것입니다. 이는 접근성을 향상시키고, 다양한 애플리케이션에서 사용자 경험을 개선하는 데 도움을 줍니다.

### 사용법
1. **객체 생성**: `SpeechSynthesisUtterance` 객체를 생성하려면 `new SpeechSynthesisUtterance(text)`를 사용합니다.
2. **속성 설정**: 음성의 속성을 설정할 수 있습니다. 예를 들어, 음성의 속도(`rate`), 피치(`pitch`), 언어(`lang`) 등을 조정할 수 있습니다.
3. **음성 합성 시작**: `speechSynthesis.speak(utterance)` 메서드를 호출하여 음성을 출력합니다.

### 세부 사항
- **속성**:
  - `text`: 읽어줄 텍스트.
  - `lang`: 언어 코드 (예: "ko-KR"은 한국어).
  - `rate`: 읽는 속도 (0.1에서 10까지의 값).
  - `pitch`: 음성의 높낮이 (0에서 2까지의 값).
  - `volume`: 음량 (0에서 1까지의 값).

- **이벤트**:
  - `onstart`: 음성 합성이 시작될 때 호출됩니다.
  - `onend`: 음성 합성이 끝날 때 호출됩니다.
  - `onerror`: 오류가 발생했을 때 호출됩니다.

## 예제
```javascript
// 새로운 SpeechSynthesisUtterance 객체 생성
const utterance = new SpeechSynthesisUtterance("안녕하세요! 자바스크립트 음성 합성 예제입니다.");

// 속성 설정
utterance.lang = 'ko-KR';
utterance.rate = 1;
utterance.pitch = 1;

// 음성 합성 시작
speechSynthesis.speak(utterance);
```

## 설명
- **브라우저 지원**: 모든 브라우저가 `SpeechSynthesisUtterance`를 지원하지 않으므로, 사용하기 전에 브라우저 호환성을 확인해야 합니다.
- **음성 선택**: 사용할 수 있는 음성의 목록은 브라우저와 운영 체제에 따라 다를 수 있습니다. `speechSynthesis.getVoices()` 메서드를 사용하여 현재 사용 가능한 음성 목록을 확인할 수 있습니다.
- **비동기 처리**: 음성 합성은 비동기적으로 작동하므로, 음성 합성이 시작되기 전에 이벤트 리스너를 설정하는 것이 좋습니다.

## 한 줄 요약
`SpeechSynthesisUtterance`는 JavaScript를 사용해 텍스트를 음성으로 변환하는 객체로, 사용자에게 읽어주는 기능을 제공합니다.