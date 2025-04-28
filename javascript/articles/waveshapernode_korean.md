<!--
Meta Description: # WaveShaperNode: 자바스크립트의 오디오 처리 기능 ## 개요 WaveShaperNode는 Web Audio API의 구성 요소로, 오디오 신호의 파형을 변형하여 다양한 효과를 생성하는 데 사용됩니다. 이를 통해 개발자는 소리의 왜곡, 텍스처 및 특성을 조...
Meta Keywords: audiocontext, curve, const, oscillator, waveshapernode
-->

# WaveShaperNode: 자바스크립트의 오디오 처리 기능

## 개요
WaveShaperNode는 Web Audio API의 구성 요소로, 오디오 신호의 파형을 변형하여 다양한 효과를 생성하는 데 사용됩니다. 이를 통해 개발자는 소리의 왜곡, 텍스처 및 특성을 조정할 수 있습니다.

## 문서화

### 목적
WaveShaperNode는 오디오 신호의 형상을 변화시켜, 사용자가 원하는 음향 효과를 만들 수 있도록 돕습니다. 이 노드는 특히 음악 제작 및 사운드 디자인에서 유용하며, 신호를 비선형적으로 처리할 수 있게 해줍니다.

### 사용법
WaveShaperNode는 다음과 같은 방법으로 생성할 수 있습니다:

```javascript
const audioContext = new AudioContext();
const waveShaperNode = audioContext.createWaveShaper();
```

WaveShaperNode는 `curve`라는 속성을 통해 오디오 신호의 변형을 정의할 수 있습니다. 예를 들어:

```javascript
const curve = new Float32Array(44100);
for (let i = 0; i < curve.length; ++i) {
    const x = (i * 2.0) / curve.length - 1; // -1.0 to 1.0
    curve[i] = Math.sin(Math.PI * x); // 사인 파형
}
waveShaperNode.curve = curve;
```

WaveShaperNode는 일반적으로 다른 오디오 노드와 연결하여 사용됩니다:

```javascript
const oscillator = audioContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime);

oscillator.connect(waveShaperNode);
waveShaperNode.connect(audioContext.destination);
oscillator.start();
```

## 예시
다음은 WaveShaperNode를 사용하여 간단한 왜곡 효과를 생성하는 예입니다:

```javascript
const audioContext = new AudioContext();
const waveShaperNode = audioContext.createWaveShaper();

const curve = new Float32Array(44100);
for (let i = 0; i < curve.length; ++i) {
    const x = (i * 2.0) / curve.length - 1; // -1.0 to 1.0
    curve[i] = (x < 0) ? 0 : x * x; // 간단한 왜곡
}
waveShaperNode.curve = curve;

const oscillator = audioContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioContext.currentTime);

oscillator.connect(waveShaperNode);
waveShaperNode.connect(audioContext.destination);
oscillator.start();
```

## 설명
WaveShaperNode를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **커브 정의**: 커브를 잘못 정의하면 원하지 않는 왜곡 효과가 발생할 수 있습니다. 다양한 함수와 수식을 사용하여 실험해 보는 것이 중요합니다.
2. **오디오 컨텍스트**: WaveShaperNode는 반드시 AudioContext 내에서 생성되어야 하며, 다른 오디오 노드와 연결하여 사용해야 합니다.
3. **리소스 관리**: AudioContext가 활성화된 동안 시스템 리소스를 소모하므로 필요하지 않을 때는 이를 종료해야 합니다.

## 한 줄 요약
WaveShaperNode는 Web Audio API를 통해 오디오 신호의 파형을 변형하여 다양한 음향 효과를 생성하는 데 사용되는 자바스크립트 노드입니다.