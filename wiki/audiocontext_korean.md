<!--
Meta Description: # AudioContext: JavaScript를 통한 웹 오디오 API의 중심 ## 개요 `AudioContext`는 웹 오디오 API의 핵심 요소로, 오디오 처리 및 생성의 기본 환경을 설정합니다. 이를 통해 다양한 오디오 작업을 수행할 수 있으며, 웹 애플리케이션...
Meta Keywords: audiocontext, 오디오, oscillator, 있습니다, javascript
-->

# AudioContext: JavaScript를 통한 웹 오디오 API의 중심

## 개요
`AudioContext`는 웹 오디오 API의 핵심 요소로, 오디오 처리 및 생성의 기본 환경을 설정합니다. 이를 통해 다양한 오디오 작업을 수행할 수 있으며, 웹 애플리케이션에서 고품질의 오디오 경험을 제공합니다.

## 문서화
### 목적
`AudioContext`는 오디오 그래프를 구성하고, 오디오 신호를 처리하기 위한 컨텍스트를 제공합니다. 이 객체는 오디오의 생성, 재생, 변형 및 분석을 가능하게 합니다.

### 사용법
`AudioContext` 객체를 생성하려면 다음과 같이 할 수 있습니다:

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
```

이 객체가 생성되면, 다양한 오디오 노드를 연결하여 복잡한 오디오 그래프를 구성할 수 있습니다. 노드에는 소스 노드, 효과 노드, 출력 노드 등이 포함됩니다.

### 세부 사항
- `AudioContext`는 비동기적으로 작동하며, 오디오를 처리하기 위해 브라우저의 오디오 하드웨어와 통신합니다.
- 다양한 메서드와 속성을 제공하여 오디오의 속성을 조정할 수 있습니다.
- `AudioContext`는 여러 개의 인스턴스를 생성할 수 있지만, 대부분의 경우 하나의 인스턴스를 사용하는 것이 가장 효율적입니다.

## 예제
기본적인 `AudioContext` 사용 예시는 다음과 같습니다:

### 1. 오디오 컨텍스트 생성 및 사운드 재생
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine'; // 사인파
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 음
oscillator.connect(audioContext.destination); // 출력 노드에 연결
oscillator.start(); // 사운드 시작
oscillator.stop(audioContext.currentTime + 1); // 1초 후 사운드 정지
```

### 2. 오디오 파일 로드 및 재생
```javascript
fetch('audio-file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    const source = audioContext.createBufferSource();
    source.buffer = buffer;
    source.connect(audioContext.destination);
    source.start();
  })
  .catch(error => console.error('Error with decoding audio data:', error));
```

## 설명
- **비동기성**: `AudioContext`는 비동기적으로 작동하므로, 관련 작업이 완료될 때까지 기다려야 할 필요가 있습니다.
- **사용자 상호작용 필요**: 대부분의 브라우저에서 오디오 재생은 사용자 상호작용(예: 클릭) 후에만 허용됩니다. 따라서, `AudioContext`를 생성하는 작업은 사용자 이벤트와 함께 진행해야 합니다.
- **메모리 관리**: 사용이 끝난 `AudioContext`는 메모리 누수를 방지하기 위해 명시적으로 종료해야 할 수 있습니다.

## 한 줄 요약
`AudioContext`는 웹 오디오 API의 기본 환경을 제공하여 고급 오디오 처리를 가능하게 하는 JavaScript 객체입니다.