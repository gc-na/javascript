<!--
Meta Description: # ScriptProcessorNode: 자바스크립트에서 오디오 프로세싱의 기본 ## 개요 `ScriptProcessorNode`는 Web Audio API의 한 구성 요소로, 사용자 정의 오디오 처리를 가능하게 하는 노드입니다. 이 노드를 사용하면 JavaScript...
Meta Keywords: 오디오, scriptprocessornode, audiocontext, const, 있습니다
-->

# ScriptProcessorNode: 자바스크립트에서 오디오 프로세싱의 기본

## 개요
`ScriptProcessorNode`는 Web Audio API의 한 구성 요소로, 사용자 정의 오디오 처리를 가능하게 하는 노드입니다. 이 노드를 사용하면 JavaScript를 통해 실시간으로 오디오 데이터를 생성하거나 수정할 수 있습니다.

## 문서화
`ScriptProcessorNode`는 오디오 신호를 처리하기 위해 사용자 정의 스크립트를 실행할 수 있는 오디오 노드입니다. 주로 오디오 애플리케이션에서 실시간 오디오 효과를 구현할 때 사용됩니다. 

### 목적
- 실시간 오디오 데이터 처리 및 생성
- 오디오 효과 적용
- 오디오 신호를 변형하거나 분석

### 사용법
`ScriptProcessorNode`는 `AudioContext.createScriptProcessor(bufferSize, numberOfInputChannels, numberOfOutputChannels)` 메서드를 통해 생성됩니다. 여기서 `bufferSize`는 오디오 버퍼의 크기, `numberOfInputChannels`와 `numberOfOutputChannels`는 각각 입력 및 출력 채널 수를 나타냅니다.

### 세부 사항
- `ScriptProcessorNode`는 비동기적으로 작동하며, 오디오 데이터를 JavaScript로 처리할 수 있는 `onaudioprocess` 이벤트 핸들러를 제공합니다.
- 이 노드는 비디오와 동시에 오디오를 처리할 때 유용합니다.
- 그러나 `ScriptProcessorNode`는 더 이상 권장되지 않으며, 대신 `AudioWorklet` 사용이 권장됩니다.

## 예제
기본적인 `ScriptProcessorNode` 사용 예시는 다음과 같습니다.

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const bufferSize = 2048;
const scriptNode = audioContext.createScriptProcessor(bufferSize, 1, 1);

scriptNode.onaudioprocess = function(event) {
    const inputBuffer = event.inputBuffer.getChannelData(0);
    const outputBuffer = event.outputBuffer.getChannelData(0);

    for (let i = 0; i < inputBuffer.length; i++) {
        // 오디오 신호를 간단히 반전
        outputBuffer[i] = -inputBuffer[i];
    }
};

scriptNode.connect(audioContext.destination);
```

## 설명
`ScriptProcessorNode`를 사용할 때 몇 가지 주의해야 할 점이 있습니다:

- **성능**: `ScriptProcessorNode`는 실시간 처리를 위한 것이지만, 높은 버퍼 크기를 사용하면 지연이 발생할 수 있습니다.
- **메모리 관리**: `onaudioprocess` 내에서 메모리 할당을 피해야 하며, 가비지 컬렉션에 영향을 줄 수 있습니다.
- **대체**: 최신 브라우저에서는 `AudioWorklet`이 더 나은 성능과 기능을 제공하므로, 새로운 프로젝트에서는 `AudioWorklet` 사용을 고려하는 것이 좋습니다.

## 한 줄 요약
`ScriptProcessorNode`는 Web Audio API의 구성 요소로, 실시간 오디오 데이터 처리를 위한 사용자 정의 노드입니다.