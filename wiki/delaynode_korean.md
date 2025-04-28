<!--
Meta Description: # DelayNode: 자바스크립트에서 오디오 지연 효과 구현하기 ## 개요 DelayNode는 Web Audio API의 일부로, 오디오 신호에 지연 효과를 추가하는 데 사용됩니다. 이 노드는 오디오 신호를 특정 시간 지연 후에 출력하여 다양한 오디오 효과를 생성할 ...
Meta Keywords: 오디오, delaynode, 효과를, delaynode를, 있습니다
-->

# DelayNode: 자바스크립트에서 오디오 지연 효과 구현하기

## 개요
DelayNode는 Web Audio API의 일부로, 오디오 신호에 지연 효과를 추가하는 데 사용됩니다. 이 노드는 오디오 신호를 특정 시간 지연 후에 출력하여 다양한 오디오 효과를 생성할 수 있도록 합니다.

## 문서화

### 목적
DelayNode는 오디오 신호의 특정 지점에 지연을 추가하여 사운드 디자인 및 음악 제작에서 중요한 역할을 합니다. 주로 에코 효과를 생성하거나 오디오 믹스에 깊이를 더하는 데 사용됩니다.

### 사용법
DelayNode를 사용하기 위해서는 Web Audio API의 AudioContext를 생성한 후, DelayNode를 인스턴스화해야 합니다. 다음은 DelayNode 생성 및 설정을 위한 기본적인 단계입니다.

1. **AudioContext 생성**: 오디오 컨텍스트를 생성합니다.
2. **DelayNode 생성**: DelayNode를 생성하고 지연 시간을 설정합니다.
3. **신호 연결**: 오디오 소스와 DelayNode를 연결합니다.
4. **출력 연결**: DelayNode의 출력을 AudioContext의 목적지에 연결합니다.

### 상세 설명
DelayNode는 생성 시, 지연 시간과 피드백을 설정할 수 있습니다. 지연 시간은 밀리초 단위로 설정되며, 피드백은 이전 신호의 일부를 다시 DelayNode에 입력하여 반복 효과를 생성합니다.

- **DelayTime**: 최대 63초까지 설정할 수 있습니다.
- **Feedback**: 0에서 1 사이의 값을 가지며, 1은 원래 신호의 전체를 다시 입력하는 것을 의미합니다.

## 예제

### 기본 사용 예제
```javascript
// AudioContext 생성
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

// DelayNode 생성
const delayNode = audioCtx.createDelay(1.0); // 1초 지연

// 오디오 소스 생성 (예: Oscillator)
const oscillator = audioCtx.createOscillator();
oscillator.frequency.setValueAtTime(440, audioCtx.currentTime); // A4 음

// 소스와 DelayNode 연결
oscillator.connect(delayNode);
delayNode.connect(audioCtx.destination);

// 오디오 재생 시작
oscillator.start();
```

## 설명
DelayNode를 사용할 때 자주 발생하는 문제와 주의할 점은 다음과 같습니다:

- **지연 시간 설정**: 지연 시간을 너무 짧게 설정하면 효과가 제대로 나타나지 않을 수 있으며, 너무 길게 설정하면 원치 않는 결과를 초래할 수 있습니다.
- **Feedback 사용**: 피드백을 과도하게 설정할 경우, 무한 반복의 결과로 인해 오디오가 왜곡될 수 있습니다.
- **오디오Context 상태**: 오디오를 재생하기 전에 AudioContext가 resume() 상태여야 합니다. 사용자가 페이지를 처음 로드할 때는 자동으로 재생되지 않을 수 있습니다.

## 한 줄 요약
DelayNode는 Web Audio API에서 오디오 신호에 지연 효과를 추가하여 다양한 사운드 효과를 생성하는 데 사용됩니다.