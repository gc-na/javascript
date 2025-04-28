<!--
Meta Description: # PannerNode: 자바스크립트에서의 3D 오디오 위치화 ## 개요 PannerNode는 Web Audio API의 구성 요소로, 3D 공간에서 소리의 위치를 제어하고 처리하는 데 사용됩니다. 이를 통해 개발자는 가상의 오디오 환경을 조성하고, 청취자가 소리를 어...
Meta Keywords: audiocontext, panner, source, 소리의, const
-->

# PannerNode: 자바스크립트에서의 3D 오디오 위치화

## 개요
PannerNode는 Web Audio API의 구성 요소로, 3D 공간에서 소리의 위치를 제어하고 처리하는 데 사용됩니다. 이를 통해 개발자는 가상의 오디오 환경을 조성하고, 청취자가 소리를 어떻게 인식할지를 조정할 수 있습니다.

## 문서화
### 목적
PannerNode는 오디오 소스의 위치를 3D 공간에서 정의하여, 소리의 방향성과 거리감을 실현합니다. 이를 통해 효과적인 가상 오디오 경험을 제공합니다.

### 사용법
PannerNode를 사용하기 위해서는 먼저 AudioContext를 생성하고, 그 안에 PannerNode를 추가해야 합니다. PannerNode는 소리의 위치, 방향, 속도 등을 제어할 수 있는 속성을 제공합니다.

#### 기본 사용법
```javascript
// AudioContext 생성
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// PannerNode 생성
const panner = audioContext.createPanner();

// PannerNode 설정
panner.panningModel = 'HRTF'; // HRTF(Head-Related Transfer Function) 모델 사용
panner.setPosition(0, 0, 0); // X, Y, Z 좌표 설정

// AudioBufferSourceNode 생성 및 연결
const source = audioContext.createBufferSource();
// source.buffer에 AudioBuffer 할당
source.connect(panner);
panner.connect(audioContext.destination);

// 재생
source.start();
```

### 세부 사항
- **panningModel**: 소리의 방향성을 결정하는 모델을 설정합니다. 지원되는 모델로는 'HRTF'와 'equalpower'가 있습니다.
- **distanceModel**: 소리의 거리 감소 모델을 설정합니다. 'linear', 'inverse', 'exponential' 중 선택할 수 있습니다.
- **refDistance**: 소리의 참 거리로, 이 거리를 기준으로 소리의 볼륨이 감소합니다.
- **maxDistance**: 소리의 최대 거리로, 이 거리를 초과하면 소리가 더 이상 들리지 않습니다.
- **rolloffFactor**: 소리가 거리에 따라 얼마나 빨리 감소하는지를 결정합니다.

## 예제
### 기본 예제
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const panner = audioContext.createPanner();

panner.setPosition(5, 0, 0); // 오른쪽에 위치 설정
panner.panningModel = 'HRTF';

const source = audioContext.createBufferSource();
// 소스에 AudioBuffer 할당
source.connect(panner);
panner.connect(audioContext.destination);
source.start();
```

### 다양한 거리 모델 사용
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const panner = audioContext.createPanner();

panner.distanceModel = 'exponential';
panner.refDistance = 1;
panner.maxDistance = 100;
panner.rolloffFactor = 5;

const source = audioContext.createBufferSource();
// source.buffer에 AudioBuffer 할당
source.connect(panner);
panner.connect(audioContext.destination);
source.start();
```

## 설명
PannerNode를 사용할 때 주의해야 할 몇 가지 사항이 있습니다. 
- **AudioContext의 상태**: AudioContext가 resume 상태가 아니면 소리가 재생되지 않을 수 있습니다. 필요시 `audioContext.resume()`을 호출하여 상태를 변경해야 합니다.
- **속성 설정**: PannerNode의 속성을 설정하는 순서에 따라 결과가 달라질 수 있습니다. 예를 들어, 소스 노드와 연결하기 전에 PannerNode의 설정을 완료해야 합니다.

## 한 줄 요약
PannerNode는 Web Audio API를 통해 3D 공간에서 소리의 위치를 제어하여 몰입감 있는 오디오 경험을 제공합니다.