<!--
Meta Description: # SpeechSynthesisVoice: 자바스크립트에서 음성 합성을 위한 음성 객체 ## 개요 `SpeechSynthesisVoice`는 자바스크립트의 Web Speech API의 일부로, 음성 합성에 사용되는 음성을 정의하는 객체입니다. 이 객체를 통해 개발자는 ...
Meta Keywords: voice, speechsynthesis, speechsynthesisvoice, utterance, 음성을
-->

# SpeechSynthesisVoice: 자바스크립트에서 음성 합성을 위한 음성 객체

## 개요
`SpeechSynthesisVoice`는 자바스크립트의 Web Speech API의 일부로, 음성 합성에 사용되는 음성을 정의하는 객체입니다. 이 객체를 통해 개발자는 다양한 음성 옵션을 설정하고, 사용자가 선택할 수 있도록 지원할 수 있습니다.

## 문서화

### 목적
`SpeechSynthesisVoice`는 웹 애플리케이션에서 텍스트를 음성으로 변환하는 기능을 구현할 때 사용됩니다. 이 객체는 사용 가능한 음성의 속성과 메타데이터를 제공합니다.

### 사용법
`SpeechSynthesisVoice` 객체는 `speechSynthesis.getVoices()` 메서드를 통해 얻을 수 있습니다. 이 메서드는 사용 가능한 모든 음성을 배열로 반환합니다. 각 음성 객체에는 다음과 같은 속성이 포함됩니다:

- `name`: 음성의 이름
- `lang`: 음성이 지원하는 언어
- `localService`: 로컬 합성 서비스 여부
- `default`: 기본 음성 여부

### 세부 사항
1. **음성 가져오기**: 
   ```javascript
   const voices = speechSynthesis.getVoices();
   ```
   이 코드는 사용 가능한 음성 목록을 가져옵니다.

2. **음성 선택**:
   ```javascript
   const selectedVoice = voices.find(voice => voice.name === 'Google 한국어');
   ```

3. **음성 합성**:
   ```javascript
   const utterance = new SpeechSynthesisUtterance('안녕하세요, 반갑습니다!');
   utterance.voice = selectedVoice;
   speechSynthesis.speak(utterance);
   ```

## 예제

### 예제 1: 모든 음성 목록 가져오기
```javascript
let voices = [];

function populateVoiceList() {
    voices = speechSynthesis.getVoices();
    voices.forEach(voice => {
        console.log(voice.name + ' (' + voice.lang + ')');
    });
}

speechSynthesis.onvoiceschanged = populateVoiceList;
```

### 예제 2: 특정 음성으로 텍스트 읽기
```javascript
const utterance = new SpeechSynthesisUtterance('웹 스피치 API를 사용하여 음성 합성을 하는 방법입니다.');
const voice = speechSynthesis.getVoices().find(v => v.name === 'Google 한국어');

if (voice) {
    utterance.voice = voice;
    speechSynthesis.speak(utterance);
}
```

## 설명
- **브라우저 호환성**: 모든 브라우저가 `SpeechSynthesisVoice`를 지원하지 않으므로, 사용하기 전에 지원 여부를 확인해야 합니다.
- **음성 로딩 지연**: `getVoices()`가 비동기적으로 음성을 로드할 수 있으므로, `onvoiceschanged` 이벤트를 사용하여 음성이 준비된 후에 작업을 진행해야 합니다.
- **언어 지원**: 일부 음성은 특정 언어에만 최적화되어 있으므로, 사용자가 선택할 수 있는 음성을 제공할 때 주의해야 합니다.

## 한 줄 요약
`SpeechSynthesisVoice`는 자바스크립트에서 텍스트를 음성으로 변환할 때 사용할 수 있는 음성 객체로, 다양한 음성을 설정하고 선택할 수 있는 기능을 제공합니다.