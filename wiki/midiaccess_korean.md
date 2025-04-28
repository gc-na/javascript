<!--
Meta Description: # MIDIAccess: JavaScript를 통한 미디어 장치 접근 ## 개요 MIDIAccess는 JavaScript를 사용하여 MIDI (Musical Instrument Digital Interface) 장치에 접근하고, 데이터를 송수신할 수 있는 기능을 제공합...
Meta Keywords: midi, midiaccess, 장치에, api는, 합니다
-->

# MIDIAccess: JavaScript를 통한 미디어 장치 접근

## 개요
MIDIAccess는 JavaScript를 사용하여 MIDI (Musical Instrument Digital Interface) 장치에 접근하고, 데이터를 송수신할 수 있는 기능을 제공합니다. 이 API는 웹 애플리케이션에서 MIDI 장치를 쉽게 사용할 수 있게 해주어 음악 제작 및 실시간 MIDI 인터랙션을 가능하게 합니다.

## 문서화
MIDIAccess API는 웹 브라우저에서 MIDI 장치에 대한 접근을 제공하는 고수준 인터페이스입니다. 이 API를 사용하면 connected MIDI 장치 목록을 가져오고, 각 장치와의 통신을 관리할 수 있습니다. MIDI 데이터는 주로 노트 정보와 컨트롤러 값으로 구성됩니다.

### 주요 기능
- **MIDI 장치 탐색**: 연결된 MIDI 장치 목록을 가져올 수 있습니다.
- **MIDI 데이터 송수신**: MIDI 메시지를 송신하고 수신할 수 있습니다.
- **장치 이벤트 리스닝**: MIDI 장치의 연결 및 해제 이벤트를 감지할 수 있습니다.

### 사용법
MIDIAccess API는 `navigator.requestMIDIAccess()` 메서드를 통해 초기화됩니다. 이 메서드는 사용자의 MIDI 장치에 대한 접근 권한을 요청합니다.

#### 기본 사용법
```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
  console.log('MIDI Access 성공:', midiAccess);
}

function onMIDIFailure() {
  console.error('MIDI Access 실패');
}
```

## 예제
### MIDI 장치 목록 가져오기
```javascript
navigator.requestMIDIAccess()
  .then(midiAccess => {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
      console.log(`MIDI Input: ${input.name}`);
    });
  });
```

### MIDI 메시지 송신하기
```javascript
navigator.requestMIDIAccess()
  .then(midiAccess => {
    const output = midiAccess.outputs.get('your-output-id');
    if (output) {
      output.send([0x90, 60, 0x7f]); // 노트 온 메시지
    }
  });
```

## 설명
MIDIAccess API를 사용할 때 주의해야 할 점은 다음과 같습니다:

1. **브라우저 지원**: 모든 웹 브라우저에서 MIDIAccess API를 지원하지 않으므로, 사용 전 지원 여부를 확인해야 합니다.
2. **사용자 권한**: MIDI 장치에 접근하기 위해서는 사용자의 명시적인 허가가 필요합니다. 사용자가 허가하지 않으면 API를 사용할 수 없습니다.
3. **정확한 장치 ID**: MIDI 출력 장치에 메시지를 보내기 위해서는 정확한 장치 ID를 알아야 합니다. 장치 목록을 통해 ID를 확인해야 합니다.

## 한 줄 요약
MIDIAccess API는 JavaScript에서 MIDI 장치에 접근하고, MIDI 데이터를 송수신하는 기능을 제공합니다.