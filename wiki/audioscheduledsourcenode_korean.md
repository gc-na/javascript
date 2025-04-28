<!--
Meta Description: # AudioScheduledSourceNode: JavaScript에서의 오디오 제어 ## 개요 `AudioScheduledSourceNode`는 Web Audio API의 일부로, 오디오 데이터를 프로그램적으로 생성하거나 재생하기 위한 기본 인터페이스입니다. 이 노...
Meta Keywords: 오디오, audiocontext, audioscheduledsourcenode, const, source
-->

# AudioScheduledSourceNode: JavaScript에서의 오디오 제어

## 개요
`AudioScheduledSourceNode`는 Web Audio API의 일부로, 오디오 데이터를 프로그램적으로 생성하거나 재생하기 위한 기본 인터페이스입니다. 이 노드는 오디오의 생성을 제어하고, 특정 시점에 오디오를 재생할 수 있는 기능을 제공합니다.

## 문서화
`AudioScheduledSourceNode`는 오디오 소스를 생성하고 관리하는 데 사용됩니다. 이 노드는 주로 `AudioBufferSourceNode`, `ConstantSourceNode`, 그리고 `MediaElementAudioSourceNode`와 같은 서브클래스를 통해 구현됩니다. 이를 통해 개발자는 다양한 오디오 소스를 생성하고, 재생 시간, 지속 시간 등을 세밀하게 조정할 수 있습니다.

### 목적
- 오디오 데이터의 생성 및 관리
- 시간에 따라 오디오를 재생하고 정지할 수 있는 기능 제공

### 사용법
`AudioScheduledSourceNode`는 직접 인스턴스를 생성할 수 없으며, 하위 클래스인 `AudioBufferSourceNode`와 같은 객체를 사용하여 인스턴스를 생성해야 합니다.

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const source = audioContext.createBufferSource();
```

## 예제
### 기본 사용 예제
아래는 오디오 파일을 로드하고 재생하는 기본 예제입니다.

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const audioElement = document.createElement('audio');
audioElement.src = 'example.mp3';

const source = audioContext.createMediaElementSource(audioElement);
source.connect(audioContext.destination);

// 오디오 재생
audioElement.play();
```

### AudioBufferSourceNode 사용 예제
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
fetch('example.mp3')
    .then(response => response.arrayBuffer())
    .then(data => audioContext.decodeAudioData(data))
    .then(buffer => {
        const source = audioContext.createBufferSource();
        source.buffer = buffer;
        source.connect(audioContext.destination);
        source.start(0); // 즉시 재생
    });
```

## 설명
`AudioScheduledSourceNode`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **상태 관리**: `AudioScheduledSourceNode`는 재생이 끝나면 자동으로 종료되며, 재생을 다시 시작하려면 새로운 인스턴스를 생성해야 합니다.
2. **오디오 컨텍스트의 상태**: 오디오 컨텍스트가 `suspended` 상태일 경우, 노드가 재생되지 않으므로 `resume()` 메서드를 호출하여 상태를 변경해야 합니다.
3. **메모리 관리**: 여러 오디오 소스를 생성할 경우, 메모리 사용량이 증가할 수 있으므로 필요하지 않은 소스는 적절히 해제해야 합니다.

## 한 문장 요약
`AudioScheduledSourceNode`는 Web Audio API에서 오디오 소스를 생성하고 제어하기 위한 기본 인터페이스로, 다양한 오디오 재생 기능을 제공합니다.