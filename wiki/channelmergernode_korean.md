<!--
Meta Description: # ChannelMergerNode: JavaScript에서의 오디오 채널 병합 노드 ## 개요 ChannelMergerNode는 Web Audio API의 일부로, 여러 개의 오디오 채널을 하나의 오디오 스트림으로 병합하는 데 사용됩니다. 이 노드는 복수의 입력 채널...
Meta Keywords: 오디오, audiocontext, 채널을, const, channelmerger
-->

# ChannelMergerNode: JavaScript에서의 오디오 채널 병합 노드

## 개요
ChannelMergerNode는 Web Audio API의 일부로, 여러 개의 오디오 채널을 하나의 오디오 스트림으로 병합하는 데 사용됩니다. 이 노드는 복수의 입력 채널을 결합하여 출력할 수 있도록 설계되어 있으며, 오디오 믹싱과 같은 다양한 오디오 처리 작업에 유용합니다.

## 문서화
ChannelMergerNode는 주로 오디오 프로세싱을 위한 그래픽 노드로, 여러 개의 오디오 소스(예: 오디오 파일, 마이크 입력 등)를 하나의 출력으로 혼합할 수 있게 해줍니다. 이 노드는 오디오 그래프의 일부로 사용되며, 생성된 노드를 통해 다양한 오디오 효과를 적용할 수 있습니다.

### 사용법
ChannelMergerNode는 AudioContext의 `createChannelMerger()` 메서드를 통해 생성할 수 있습니다. 기본적으로 2개에서 6개까지의 입력 채널을 지원합니다.

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const channelMerger = audioContext.createChannelMerger(2); // 2채널 병합
```

이제 병합하려는 오디오 소스를 이 노드의 입력으로 연결할 수 있습니다. 연결 후, 최종 출력은 `channelMerger` 노드를 통해 가져올 수 있습니다.

## 예제
아래는 두 개의 오디오 소스를 병합하는 기본 예제입니다.

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 두 개의 오디오 소스 생성
const source1 = audioContext.createBufferSource();
const source2 = audioContext.createBufferSource();

// ChannelMergerNode 생성
const channelMerger = audioContext.createChannelMerger(2);

// 오디오 소스와 병합 노드 연결
source1.connect(channelMerger, 0, 0); // 첫 번째 소스의 첫 번째 채널을 병합 노드의 첫 번째 채널에 연결
source2.connect(channelMerger, 0, 1); // 두 번째 소스의 첫 번째 채널을 병합 노드의 두 번째 채널에 연결

// 최종 출력을 오디오 컨텍스트의 출력에 연결
channelMerger.connect(audioContext.destination);

// 소스 재생
source1.start();
source2.start();
```

## 설명
ChannelMergerNode를 사용할 때 유의해야 할 몇 가지 사항이 있습니다:

1. **채널 수 제한**: 최대 6개 채널을 병합할 수 있으며, 이 수를 초과하면 오류가 발생합니다.
2. **오디오 컨텍스트 상태**: 오디오 컨텍스트가 `suspended` 상태일 때는 소스 노드를 시작할 수 없습니다. 반드시 `resume()` 메서드를 호출하여 컨텍스트를 활성화해야 합니다.
3. **비동기 처리**: 오디오 소스가 비동기적으로 로드될 수 있으므로, 버퍼를 로드한 후에 `start()` 메서드를 호출해야 합니다.

## 한 줄 요약
ChannelMergerNode는 여러 오디오 소스를 하나로 병합하여 출력하기 위한 Web Audio API의 구성 요소입니다.