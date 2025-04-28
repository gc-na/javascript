<!--
Meta Description: # BaseAudioContext: 자바스크립트에서의 오디오 컨텍스트의 기본 ## 개요 `BaseAudioContext`는 웹 오디오 API의 핵심 구성 요소로, 오디오 프로세싱을 위한 컨텍스트를 제공합니다. 이 인터페이스는 오디오 그래프의 생성 및 관리에 필요한 다양...
Meta Keywords: 오디오, baseaudiocontext, 컨텍스트를, audiocontext, audioctx
-->

# BaseAudioContext: 자바스크립트에서의 오디오 컨텍스트의 기본

## 개요
`BaseAudioContext`는 웹 오디오 API의 핵심 구성 요소로, 오디오 프로세싱을 위한 컨텍스트를 제공합니다. 이 인터페이스는 오디오 그래프의 생성 및 관리에 필요한 다양한 기능을 제공합니다.

## 문서화

### 목적
`BaseAudioContext`는 오디오 데이터를 생성하고 처리하기 위한 환경을 설정하는 역할을 합니다. 이를 통해 개발자는 다양한 오디오 소스를 연결하고, 효과를 적용하며, 최종적으로 오디오 출력을 생성할 수 있습니다.

### 사용법
`BaseAudioContext`는 직접 인스턴스화할 수 없으며, 이를 상속받은 `AudioContext`와 `OfflineAudioContext`를 사용하여 생성됩니다. 오디오 컨텍스트를 생성한 후, 다양한 오디오 노드를 추가하고 연결하여 복잡한 오디오 처리를 수행할 수 있습니다.

#### 기본 구문
```javascript
const audioCtx = new AudioContext(); // AudioContext 인스턴스 생성
```

### 세부 사항
- **속성**: `BaseAudioContext`는 다양한 속성을 포함하고 있으며, 그 중 몇 가지는 다음과 같습니다.
  - `sampleRate`: 오디오 샘플링 레이트를 반환합니다.
  - `state`: 컨텍스트의 현재 상태를 나타냅니다 (예: 'suspended', 'running', 'closed').
  
- **메서드**: `BaseAudioContext`는 여러 메서드를 제공합니다.
  - `suspend()`: 오디오 컨텍스트를 일시 중지합니다.
  - `resume()`: 일시 중지된 오디오 컨텍스트를 재개합니다.
  - `close()`: 오디오 컨텍스트를 닫고 리소스를 해제합니다.

## 예제
### 기본 사용 예
```javascript
// AudioContext 생성
const audioCtx = new AudioContext();

// 오디오 소스 노드 생성
const oscillator = audioCtx.createOscillator();
oscillator.type = 'sine'; // 파형 타입 설정
oscillator.frequency.setValueAtTime(440, audioCtx.currentTime); // 주파수 설정

// 소스 노드를 컨텍스트에 연결
oscillator.connect(audioCtx.destination);
oscillator.start(); // 발음 시작
```

## 설명
- **일반적인 문제점**: `BaseAudioContext`를 사용할 때 가장 흔한 문제는 컨텍스트의 상태 관리입니다. 예를 들어, `suspend()` 메서드를 호출한 후에는 반드시 `resume()` 메서드로 다시 시작해야 합니다. 또한, 컨텍스트가 닫힌 상태에서 메서드를 호출하면 오류가 발생합니다.
- **브라우저 호환성**: 모든 주요 브라우저에서 지원되지만, 특정 기능은 브라우저마다 다를 수 있으므로 항상 최신 문서를 참조하는 것이 좋습니다.

## 한 문장 요약
`BaseAudioContext`는 웹 오디오 API에서 오디오 프로세싱을 위한 기본 오디오 컨텍스트를 제공하는 핵심 인터페이스입니다.