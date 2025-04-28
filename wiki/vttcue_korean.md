<!--
Meta Description: # VTTCue: 자바스크립트에서의 사용법과 예제 ## 개요 VTTCue는 HTML5 비디오와 자막을 다루기 위한 JavaScript API의 일부로, 웹 애플리케이션에서 텍스트 트랙을 정의하고 조작하는 데 사용됩니다. ## 문서화 VTTCue 객체는 비디오에서 자막 ...
Meta Keywords: vttcue, 텍스트, vttcue는, text, cue
-->

# VTTCue: 자바스크립트에서의 사용법과 예제

## 개요
VTTCue는 HTML5 비디오와 자막을 다루기 위한 JavaScript API의 일부로, 웹 애플리케이션에서 텍스트 트랙을 정의하고 조작하는 데 사용됩니다.

## 문서화
VTTCue 객체는 비디오에서 자막 또는 텍스트 트랙의 특정 구간을 나타내며, 텍스트의 시작 및 종료 시간, 텍스트 내용 등의 정보를 포함합니다. 이 객체는 WebVTT (Web Video Text Tracks) 포맷을 따르며, 자막 기능을 구현할 때 매우 유용합니다.

### 목적
VTTCue는 자막 데이터의 구조를 정의하고, 비디오 플레이어에서 자막을 표시할 때 필요한 정보를 제공합니다. 이를 통해 사용자는 비디오 콘텐츠를 보다 잘 이해할 수 있습니다.

### 사용법
VTTCue는 다음과 같은 속성과 메서드를 가집니다:
- **startTime**: 자막이 시작되는 시간 (초 단위).
- **endTime**: 자막이 끝나는 시간 (초 단위).
- **text**: 자막에 표시될 텍스트 내용.

### 생성자
```javascript
let cue = new VTTCue(startTime, endTime, text);
```

## 예제
다음은 VTTCue 객체를 생성하고 사용하는 기본적인 예제입니다.

```javascript
// 새로운 VTTCue 생성
let cue = new VTTCue(0, 10, "안녕하세요! 이 비디오를 시청해 주셔서 감사합니다.");

// VTTCue 속성 접근
console.log(cue.startTime); // 0
console.log(cue.endTime);   // 10
console.log(cue.text);      // "안녕하세요! 이 비디오를 시청해 주셔서 감사합니다."
```

## 설명
VTTCue를 사용할 때 주의해야 할 점:
- **시간 단위**: startTime과 endTime은 초 단위로 설정해야 하며, startTime은 항상 endTime보다 작아야 합니다.
- **텍스트 형식**: VTTCue의 text 속성은 HTML 형식을 지원하지 않으므로, HTML 태그를 포함하면 안 됩니다.
- **브라우저 호환성**: VTTCue는 HTML5를 지원하는 최신 브라우저에서 동작합니다. 구버전 브라우저에서는 지원되지 않을 수 있습니다.

## 한 줄 요약
VTTCue는 HTML5 비디오에서 자막과 텍스트 트랙을 정의하고 조작하기 위한 JavaScript 객체입니다.