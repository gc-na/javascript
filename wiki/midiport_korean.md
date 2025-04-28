<!--
Meta Description: # MIDIPort: JavaScript에서 MIDI 포트 다루기 ## 개요 MIDIPort는 JavaScript를 사용하여 MIDI(Musical Instrument Digital Interface) 장치와 상호작용할 수 있도록 해주는 Web MIDI API의 구성 ...
Meta Keywords: midi, 있습니다, web, midiport는, 포트에
-->

# MIDIPort: JavaScript에서 MIDI 포트 다루기

## 개요
MIDIPort는 JavaScript를 사용하여 MIDI(Musical Instrument Digital Interface) 장치와 상호작용할 수 있도록 해주는 Web MIDI API의 구성 요소입니다. 이 객체는 MIDI 입력 및 출력 포트를 나타내며, 개발자가 MIDI 데이터를 송수신할 수 있게 해줍니다.

## 문서화
### 목적
MIDIPort는 웹 애플리케이션에서 MIDI 장치와 통신하기 위한 인터페이스를 제공합니다. 이를 통해 사용자들은 MIDI 컨트롤러, 신디사이저 등과 쉽게 연결하여 음악 및 오디오 애플리케이션을 개발할 수 있습니다.

### 사용법
MIDIPort는 Web MIDI API의 일부분으로, `navigator.requestMIDIAccess()` 메서드를 통해 액세스할 수 있습니다. 이 메서드는 MIDI 포트에 대한 정보를 포함하는 `MIDIAccess` 객체를 반환하며, 이 객체에서 입력 및 출력 포트를 가져올 수 있습니다.

#### 기본 사용 예제
```javascript
navigator.requestMIDIAccess()
  .then((midiAccess) => {
    const inputs = midiAccess.inputs;
    const outputs = midiAccess.outputs;

    // 입력 포트 나열
    for (let input of inputs.values()) {
      console.log(`Input Port: ${input.name}`);
    }

    // 출력 포트 나열
    for (let output of outputs.values()) {
      console.log(`Output Port: ${output.name}`);
    }
  })
  .catch((error) => {
    console.error('MIDI Access Failed', error);
  });
```

## 설명
### 일반적인 함정 및 주의사항
- **브라우저 호환성**: Web MIDI API는 모든 브라우저에서 지원되지 않을 수 있습니다. Chrome 및 Opera와 같은 Chromium 기반 브라우저에서 주로 지원됩니다.
- **HTTPS 필요**: Web MIDI API를 사용하려면 안전한 연결(HTTPS)이 필요합니다. 로컬에서 테스트할 때는 `localhost`를 사용할 수 있습니다.
- **MIDI 장치 연결**: MIDI 포트에 연결하기 전에 사용자에게 권한을 요청해야 하며, 사용자가 권한을 부여하지 않으면 포트에 접근할 수 없습니다.
- **이벤트 리스너**: MIDI 포트에서 메시지를 수신하려면 입력 포트에 이벤트 리스너를 추가해야 합니다. 예를 들어, `input.onmidimessage`를 사용하여 MIDI 메시지를 처리할 수 있습니다.

### 추가 노트
MIDIPort 객체는 각 포트의 이름, ID 및 상태를 포함합니다. 이를 통해 개발자는 다양한 MIDI 장치 간에 쉽게 전환하고 관리할 수 있습니다. 또한, MIDI 메시지의 구조를 이해하는 것이 중요하며, 일반적인 메시지 타입에는 노트 온, 노트 오프, 컨트롤 체인지 등이 있습니다.

## 한 줄 요약
MIDIPort는 JavaScript에서 MIDI 입력 및 출력 포트를 다루기 위한 Web MIDI API의 핵심 구성 요소입니다.