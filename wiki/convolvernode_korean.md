<!--
Meta Description: # ConvolverNode: JavaScript의 오디오 처리 기능 ## 개요 ConvolverNode는 Web Audio API의 한 부분으로, 오디오 신호에 임펄스 응답 필터를 적용하여 리버브 효과를 생성하는 데 사용됩니다. 이 노드는 다양한 오디오 신호의 음색을...
Meta Keywords: 오디오, 임펄스, audiocontext, buffer, convolvernode
-->

# ConvolverNode: JavaScript의 오디오 처리 기능

## 개요
ConvolverNode는 Web Audio API의 한 부분으로, 오디오 신호에 임펄스 응답 필터를 적용하여 리버브 효과를 생성하는 데 사용됩니다. 이 노드는 다양한 오디오 신호의 음색을 변화시키고, 현실감 있는 오디오 경험을 제공합니다.

## 문서화
ConvolverNode는 Web Audio API의 오디오 그래프에서 사용할 수 있는 노드로, 주로 오디오 신호에 공간적인 효과를 주기 위해 사용됩니다. 사용자는 ConvolverNode를 통해 특정 공간의 음향을 모델링할 수 있으며, 이를 위해 임펄스 응답(IR) 오디오 버퍼를 로드하여 사용합니다.

### 주요 속성 및 메서드
- **buffer**: ConvolverNode에 적용할 임펄스 응답을 담고 있는 AudioBuffer 객체입니다.
- **normalize**: boolean 값, true로 설정하면 임펄스 응답을 정규화합니다.
- **connect()**: 다른 오디오 노드와 연결할 수 있는 메서드입니다.
- **disconnect()**: 연결을 해제하는 메서드입니다.

### 사용법
1. **AudioContext 생성**: Web Audio API를 사용하기 위해 AudioContext를 생성합니다.
2. **ConvolverNode 인스턴스 생성**: AudioContext의 `createConvolver()` 메서드를 호출하여 ConvolverNode를 생성합니다.
3. **임펄스 응답 로드**: AudioBufferSourceNode를 사용하여 임펄스 응답 파일을 로드합니다.
4. **노드 연결**: ConvolverNode와 다른 오디오 노드를 연결합니다.
5. **재생**: 연결된 오디오를 재생하여 리버브 효과 확인.

## 예제
```javascript
// 1. AudioContext 생성
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 2. ConvolverNode 생성
const convolver = audioContext.createConvolver();

// 3. 임펄스 응답 로드
fetch('path/to/impulse-response.wav')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    convolver.buffer = buffer;

    // 4. AudioBufferSourceNode 생성
    const source = audioContext.createBufferSource();
    source.buffer = buffer; // 여기서 buffer는 다른 음원입니다.

    // 5. 노드 연결
    source.connect(convolver);
    convolver.connect(audioContext.destination);

    // 6. 재생
    source.start();
  })
  .catch(error => console.error('Error loading impulse response:', error));
```

## 설명
ConvolverNode 사용 시 주의할 점은 임펄스 응답 파일의 형식과 크기입니다. 너무 큰 파일을 사용할 경우 성능 저하가 발생할 수 있으며, 적절한 형식(WAV 또는 AIFF)으로 준비해야 합니다. 또한, normalize 속성을 true로 설정하면 리버브 효과가 더욱 자연스럽게 들리지만, 필요에 따라 false로 설정할 수도 있습니다.

## 한 줄 요약
ConvolverNode는 Web Audio API에서 임펄스 응답을 통해 오디오 신호에 리버브 효과를 추가하는 노드입니다.