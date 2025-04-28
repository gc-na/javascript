<!--
Meta Description: # 오실레이터 노드 (OscillatorNode) - 자바스크립트에서의 오디오 신호 생성 ## 개요 오실레이터 노드는 Web Audio API의 중요한 구성 요소로, 주파수를 기반으로 한 주기적인 오디오 신호를 생성하는 데 사용됩니다. 이 노드는 다양한 주파수의 사인파...
Meta Keywords: 오실레이터, oscillator, audiocontext, 노드를, 오디오
-->

# 오실레이터 노드 (OscillatorNode) - 자바스크립트에서의 오디오 신호 생성

## 개요
오실레이터 노드는 Web Audio API의 중요한 구성 요소로, 주파수를 기반으로 한 주기적인 오디오 신호를 생성하는 데 사용됩니다. 이 노드는 다양한 주파수의 사인파, 사각파, 삼각파 및 화이트 노이즈를 생성할 수 있어, 음악 및 사운드 디자인에 유용합니다.

## 문서화

### 목적
오실레이터 노드는 오디오 신호를 생성하기 위해 사용되며, 주로 음성 합성, 게임 사운드 효과 및 음악 제작에 활용됩니다. 개발자는 이 노드를 사용하여 일정한 주파수의 음파를 생성하고, 이를 다른 오디오 노드와 연결하여 다양한 음향 효과를 만들 수 있습니다.

### 사용법
오실레이터 노드를 사용하기 위해서는 먼저 `AudioContext`를 생성하고, 그 후 `createOscillator()` 메서드를 호출하여 오실레이터 노드를 생성합니다. 기본적인 설정 후에는 `start()` 메서드로 노드를 시작하고 `stop()` 메서드로 노드를 정지시킬 수 있습니다.

#### 주요 속성 및 메서드
- `frequency`: 오실레이터의 주파수를 설정하는 속성입니다.
- `type`: 오실레이터의 파형을 설정하는 속성입니다. (예: 'sine', 'square', 'triangle', 'sawtooth')
- `start()`: 오실레이터 노드를 시작합니다.
- `stop()`: 오실레이터 노드를 정지합니다.

## 예제

### 기본 사용 예제
```javascript
// 오디오 컨텍스트 생성
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 오실레이터 노드 생성
const oscillator = audioContext.createOscillator();

// 오실레이터의 주파수 설정
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 음

// 오실레이터 타입 설정
oscillator.type = 'sine';

// 오실레이터 노드 연결 (출력)
oscillator.connect(audioContext.destination);

// 노드 시작 및 정지
oscillator.start();
setTimeout(() => {
    oscillator.stop();
}, 1000); // 1초 후 정지
```

### 다양한 파형 예제
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

const oscillator = audioContext.createOscillator();
oscillator.type = 'square'; // 사각파

oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 음
oscillator.connect(audioContext.destination);
oscillator.start();
setTimeout(() => {
    oscillator.stop();
}, 1000);
```

## 설명
오실레이터 노드를 사용할 때 주의해야 할 점은 주파수 및 타입 설정입니다. 주파수가 너무 높거나 낮으면 청각적으로 불쾌할 수 있으며, 특정 파형에 따라 신호의 특성이 달라질 수 있습니다. 또한, 노드를 시작하기 전에 반드시 오디오 컨텍스트가 활성화되어 있어야 하며, 브라우저의 자동 재생 정책에 따라 사용자 상호작용 없이 오디오가 재생되지 않을 수 있습니다.

## 한 줄 요약
오실레이터 노드는 Web Audio API를 통해 주파수를 기반으로 한 주기적인 오디오 신호를 생성하는 데 사용되는 자바스크립트 기능입니다.