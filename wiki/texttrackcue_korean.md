<!--
Meta Description: # TextTrackCue: 자바스크립트에서의 텍스트 트랙 큐 ## 개요 `TextTrackCue`는 HTML5 비디오 및 오디오 요소에서 자막과 같은 텍스트 트랙을 생성하고 조작하는 데 사용되는 JavaScript 객체입니다. 이 객체는 자막의 시작과 끝 시간, 텍스...
Meta Keywords: texttrackcue, 텍스트, 있습니다, javascript, starttime
-->

# TextTrackCue: 자바스크립트에서의 텍스트 트랙 큐

## 개요
`TextTrackCue`는 HTML5 비디오 및 오디오 요소에서 자막과 같은 텍스트 트랙을 생성하고 조작하는 데 사용되는 JavaScript 객체입니다. 이 객체는 자막의 시작과 끝 시간, 텍스트 내용 등을 정의합니다.

## 문서화
### 목적
`TextTrackCue`는 비디오 재생 중에 사용자에게 표시할 텍스트 트랙의 단일 요소를 나타냅니다. 주로 자막, 설명, 챕터 등을 생성하고 관리하는 데 쓰입니다.

### 사용법
`TextTrackCue` 객체는 다음과 같은 속성을 가집니다:

- `startTime`: 큐가 시작되는 시간(초 단위).
- `endTime`: 큐가 끝나는 시간(초 단위).
- `text`: 사용자에게 표시될 텍스트 내용.
- `id`: 선택적으로 큐의 고유 식별자.

#### 생성
`TextTrackCue` 객체는 다음과 같이 생성할 수 있습니다:

```javascript
const cue = new TextTrackCue(startTime, endTime, text);
```

여기서 `startTime`, `endTime`, `text`는 각각 시작 시간, 종료 시간, 텍스트 내용을 나타냅니다.

### 상세 정보
`TextTrackCue`는 주로 HTMLMediaElement의 `TextTrack`과 함께 사용됩니다. 이를 통해 비디오에 자막을 추가하고 제어할 수 있습니다. 자막이 재생되는 동안, 각 `TextTrackCue`는 설정된 시간에 따라 자동으로 표시되고 숨겨집니다.

## 예제
아래는 `TextTrackCue`의 기본 사용 예제입니다:

```javascript
// 비디오 요소 선택
const video = document.querySelector('video');
const textTrack = video.addTextTrack('subtitles', 'English Subtitles', 'en');

// 새로운 큐 생성
const cue = new TextTrackCue(0, 5, 'Hello, World!');

// 큐 추가
textTrack.addCue(cue);
```

이 예제는 비디오의 첫 5초 동안 "Hello, World!"라는 자막을 표시하는 큐를 생성합니다.

## 설명
`TextTrackCue`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **시간 범위**: `startTime`은 `endTime`보다 항상 작아야 합니다. 그렇지 않으면 오류가 발생합니다.
- **텍스트 길이**: 표시할 텍스트의 길이에 따라 자막이 잘리거나 화면에 적절히 표시되지 않을 수 있습니다.
- **브라우저 호환성**: 모든 브라우저에서 `TextTrackCue`에 대한 지원이 동일하지 않을 수 있습니다. 최신 브라우저에서의 사용을 권장합니다.

## 한 줄 요약
`TextTrackCue`는 HTML5 비디오에서 자막과 같은 텍스트 트랙을 생성하고 관리하는 JavaScript 객체입니다.