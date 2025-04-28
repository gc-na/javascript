<!--
Meta Description: # StereoPannerNode: 자바스크립트에서 스테레오 패닝을 구현하는 방법 ## 개요 `StereoPannerNode`는 Web Audio API의 일부로서, 오디오 소스의 스테레오 패닝을 조정하는 데 사용됩니다. 이 노드를 통해 사용자는 소리의 위치를 좌우로 ...
Meta Keywords: stereopannernode, 오디오, audiocontext, 스테레오, const
-->

# StereoPannerNode: 자바스크립트에서 스테레오 패닝을 구현하는 방법

## 개요
`StereoPannerNode`는 Web Audio API의 일부로서, 오디오 소스의 스테레오 패닝을 조정하는 데 사용됩니다. 이 노드를 통해 사용자는 소리의 위치를 좌우로 조절하여 더욱 몰입감 있는 오디오 환경을 제공합니다.

## 문서화
### 목적
`StereoPannerNode`는 오디오 소스의 위치를 스테레오 필드 내에서 조정할 수 있도록 하는 기능을 제공합니다. 이를 통해 사용자는 소리가 왼쪽 또는 오른쪽 스피커에서 더 크게 들리도록 설정할 수 있습니다.

### 사용법
1. **노드 생성**: `AudioContext` 인스턴스를 생성한 후, `createStereoPanner()` 메서드를 호출하여 `StereoPannerNode` 인스턴스를 생성합니다.
2. **속성 설정**: `pan` 속성을 사용하여 패닝 값을 설정합니다. 이 값은 -1(왼쪽)에서 1(오른쪽) 사이의 범위를 가집니다.
3. **연결**: 생성한 `StereoPannerNode`를 오디오 소스와 연결하고, 최종적으로 출력(destination)과 연결합니다.

### 속성
- `pan`: 오디오의 패닝 값을 설정하는 속성으로, -1(왼쪽)에서 1(오른쪽) 사이의 값을 가집니다. 기본값은 0(가운데)입니다.

## 예제
```javascript
// AudioContext 생성
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 오디오 소스 생성
const audioElement = new Audio('sample.mp3');
const sourceNode = audioContext.createMediaElementSource(audioElement);

// StereoPannerNode 생성
const pannerNode = audioContext.createStereoPanner();

// 패닝 값 설정
pannerNode.pan.value = -1; // 왼쪽으로 패닝

// 노드 연결
sourceNode.connect(pannerNode);
pannerNode.connect(audioContext.destination);

// 오디오 재생
audioElement.play();
```

## 설명
`StereoPannerNode`를 사용할 때 주의해야 할 점은 패닝 값이 너무 극단적으로 설정되면 소리가 한쪽으로 너무 치우쳐 들릴 수 있다는 것입니다. 또한, 패닝 효과는 오디오의 음질과 방향성을 극대화하기 위해 다양한 오디오 환경에서 테스트해야 합니다. 

가끔 브라우저의 호환성 문제로 인해 특정 기능이 예상치 못한 방식으로 작동할 수 있으므로, 항상 최신 브라우저에서 테스트하는 것이 좋습니다.

## 한 줄 요약
`StereoPannerNode`는 Web Audio API를 통해 오디오 소스의 스테레오 패닝을 손쉽게 조정할 수 있는 기능을 제공합니다.