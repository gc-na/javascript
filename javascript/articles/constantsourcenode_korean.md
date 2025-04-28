<!--
Meta Description: # ConstantSourceNode: JavaScript의 오디오 컨텍스트에서의 상수 소스 노드 ## 개요 `ConstantSourceNode`는 Web Audio API의 일부로, 일정한 주파수와 진폭을 가진 오디오 신호를 생성하는 데 사용됩니다. 이 노드는 오디오...
Meta Keywords: constantsourcenode, 오디오, audiocontext, 신호를, 노드는
-->

# ConstantSourceNode: JavaScript의 오디오 컨텍스트에서의 상수 소스 노드

## 개요
`ConstantSourceNode`는 Web Audio API의 일부로, 일정한 주파수와 진폭을 가진 오디오 신호를 생성하는 데 사용됩니다. 이 노드는 오디오 그래프의 소스로 사용되며, 주로 사운드 효과나 지속적인 오디오를 생성하는 데 유용합니다.

## 문서화
### 목적
`ConstantSourceNode`는 지속적으로 일정한 오디오 신호를 생성하여, 다양한 오디오 효과 및 상호작용을 가능하게 합니다. 이 노드는 주로 테스트 용도로 사용되거나, 다른 오디오 노드에 신호를 공급하는 데 활용됩니다.

### 사용법
`ConstantSourceNode`를 사용하려면, 먼저 `AudioContext`를 생성한 후, 해당 컨텍스트의 `createConstantSource()` 메서드를 호출하여 인스턴스를 생성합니다. 생성된 노드는 `start()` 메서드를 통해 실행할 수 있습니다.

### 속성
- `offset`: 생성되는 오디오 신호의 진폭을 설정합니다. 기본값은 0입니다.

### 메서드
- `start(when)`: 노드를 시작합니다. `when` 파라미터를 사용하여 시작 시간을 지정할 수 있습니다.
- `stop(when)`: 노드를 중지합니다.

## 예제
```javascript
// AudioContext 생성
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// ConstantSourceNode 생성
const constantSource = audioContext.createConstantSource();

// 오프셋 설정
constantSource.offset.value = 0.5; // 진폭을 0.5로 설정

// 노드 연결
constantSource.connect(audioContext.destination);

// 노드 시작
constantSource.start();
```

## 설명
`ConstantSourceNode`를 사용할 때 주의할 점은 다음과 같습니다:
- 이 노드는 항상 오디오를 출력하므로, 필요하지 않은 경우 `stop()` 메서드를 사용하여 노드를 중지해야 합니다.
- `ConstantSourceNode`는 한 번 시작하면 계속해서 오디오를 생성하므로, 다른 노드와의 연결을 통해 다양한 효과를 주어야 합니다.
- 브라우저 호환성에 유의해야 하며, Web Audio API를 지원하지 않는 브라우저에서는 사용할 수 없습니다.

## 한줄 요약
`ConstantSourceNode`는 일정한 주파수와 진폭의 오디오 신호를 생성하는 Web Audio API의 노드입니다.