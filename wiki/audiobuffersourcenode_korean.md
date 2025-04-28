<!--
Meta Description: # AudioBufferSourceNode: 자바스크립트에서 오디오 버퍼 소스 노드 활용하기 ## 개요 AudioBufferSourceNode는 Web Audio API의 중요한 구성 요소로, 메모리에 로드된 오디오 데이터를 재생하는 데 사용되는 노드입니다. 이 노드를...
Meta Keywords: 오디오, audiocontext, source, audiobuffer, const
-->

# AudioBufferSourceNode: 자바스크립트에서 오디오 버퍼 소스 노드 활용하기

## 개요
AudioBufferSourceNode는 Web Audio API의 중요한 구성 요소로, 메모리에 로드된 오디오 데이터를 재생하는 데 사용되는 노드입니다. 이 노드를 사용하면 개발자는 오디오 파일을 효과적으로 제어하고, 다양한 애플리케이션에서 오디오를 재생할 수 있습니다.

## 문서화
AudioBufferSourceNode는 Web Audio API의 일부로, 오디오를 재생하기 위해 AudioBuffer 객체를 사용하는 노드입니다. 이 노드는 단일 재생만 지원하며, 재생이 끝난 후에는 더 이상 재사용할 수 없습니다.

### 목적
AudioBufferSourceNode는 다음과 같은 목적을 가지고 있습니다:
- 메모리 내의 오디오 데이터를 재생합니다.
- 다양한 오디오 효과와 결합하여 복잡한 오디오 환경을 생성합니다.

### 사용법
AudioBufferSourceNode를 사용하기 위해서는 다음 단계가 필요합니다:

1. 오디오 컨텍스트 생성:
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   ```

2. AudioBuffer 객체 생성:
   ```javascript
   const audioBuffer = await audioContext.decodeAudioData(arrayBuffer);
   ```

3. AudioBufferSourceNode 생성 및 설정:
   ```javascript
   const source = audioContext.createBufferSource();
   source.buffer = audioBuffer;
   ```

4. 재생 시작:
   ```javascript
   source.connect(audioContext.destination);
   source.start();
   ```

### 세부사항
- **속성**: 
  - `buffer`: 재생할 AudioBuffer를 설정합니다.
  - `loop`: 노드를 반복 재생할지 여부를 설정합니다.
  
- **메서드**:
  - `start([when], [offset], [duration])`: 오디오 재생을 시작합니다.
  - `stop([when])`: 오디오 재생을 중지합니다.

## 예제
다음은 AudioBufferSourceNode를 사용하는 기본적인 예제입니다:

```javascript
async function playAudio(arrayBuffer) {
    const audioContext = new (window.AudioContext || window.webkitAudioContext)();
    const audioBuffer = await audioContext.decodeAudioData(arrayBuffer);
    
    const source = audioContext.createBufferSource();
    source.buffer = audioBuffer;
    source.connect(audioContext.destination);
    source.start();
}
```

## 설명
AudioBufferSourceNode를 사용할 때 주의해야 할 사항:
- 노드는 한 번만 재생할 수 있으며, 재생이 끝난 후에는 다시 사용할 수 없습니다. 새로운 인스턴스를 생성해야 합니다.
- AudioBufferSourceNode의 `loop` 속성이 true로 설정된 경우, 노드는 무한 반복됩니다.
- Web Audio API의 비동기적 특성으로 인해, 오디오 파일을 로드하는 동안 UI가 멈추지 않도록 해야 합니다.

## 한 줄 요약
AudioBufferSourceNode는 Web Audio API에서 메모리 내 오디오 데이터를 재생하는 데 사용되는 단일 재생 노드입니다.