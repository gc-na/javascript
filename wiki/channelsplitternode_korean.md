<!--
Meta Description: # ChannelSplitterNode: JavaScript의 오디오 처리 기능 ## 개요 ChannelSplitterNode는 Web Audio API의 구성 요소로, 오디오 트랙을 여러 개의 채널로 분리하여 각각의 채널을 독립적으로 처리할 수 있게 해줍니다. 이 노...
Meta Keywords: audiocontext, const, splitter, 오디오, connect
-->

# ChannelSplitterNode: JavaScript의 오디오 처리 기능

## 개요
ChannelSplitterNode는 Web Audio API의 구성 요소로, 오디오 트랙을 여러 개의 채널로 분리하여 각각의 채널을 독립적으로 처리할 수 있게 해줍니다. 이 노드는 주로 멀티채널 오디오 처리 및 믹싱에 사용됩니다.

## 문서화
ChannelSplitterNode는 오디오 신호를 여러 채널로 나누는 데 사용됩니다. 이 노드는 특정 오디오 소스에서 입력된 신호를 받아 각 채널로 분리하여 출력합니다. 예를 들어, 스테레오 오디오 신호는 두 개의 채널(왼쪽 및 오른쪽)로 분리됩니다.

### 사용법
ChannelSplitterNode는 Web Audio API의 AudioContext 객체를 통해 생성됩니다. 사용자는 생성 시 분리할 채널 수를 지정할 수 있습니다. 기본적으로 최대 6개의 채널을 지원하지만, 구현에 따라 다를 수 있습니다.

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const splitter = audioContext.createChannelSplitter(2); // 스테레오 분리
```

## 예제
1. 기본적인 ChannelSplitterNode 사용 예제:

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const audioElement = new Audio('path/to/audio/file.mp3');
const source = audioContext.createMediaElementSource(audioElement);
const splitter = audioContext.createChannelSplitter(2);

source.connect(splitter);
splitter.connect(audioContext.destination, 0); // 왼쪽 채널
splitter.connect(audioContext.destination, 1); // 오른쪽 채널

audioElement.play();
```

2. 각각의 채널에 필터를 적용하는 예제:

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const sourceNode = audioContext.createBufferSource();
const splitter = audioContext.createChannelSplitter(2);
const gainNode = audioContext.createGain();

sourceNode.connect(splitter);
splitter.connect(gainNode, 0); // 왼쪽 채널
splitter.connect(gainNode, 1); // 오른쪽 채널

gainNode.gain.value = 0.5; // 볼륨 조절
gainNode.connect(audioContext.destination);

sourceNode.start();
```

## 설명
ChannelSplitterNode를 사용할 때 유의해야 할 점은, 분리된 각 채널의 연결을 적절히 설정해야 한다는 것입니다. 각 채널은 독립적으로 처리되며, 연결을 누락하면 원하는 효과를 얻지 못할 수 있습니다. 또한, 생성된 ChannelSplitterNode는 AudioContext가 활성화된 상태에서만 작동하므로, 오디오 컨텍스트를 올바르게 설정하고 시작해야 합니다.

또한, ChannelSplitterNode는 생성 시 지정된 채널 수만큼만 작동하므로, 필요하지 않은 채널을 생성하지 않도록 유의해야 합니다.

## 한 줄 요약
ChannelSplitterNode는 Web Audio API에서 오디오 신호를 여러 채널로 분리하여 독립적으로 처리할 수 있는 기능을 제공합니다.