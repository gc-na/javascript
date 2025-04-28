<!--
Meta Description: # MIDIInput: 자바스크립트에서 MIDI 장치와의 상호작용 ## 개요 MIDIInput은 웹 오디오 API의 일부분으로, 브라우저에서 MIDI 장치와의 상호작용을 가능하게 해줍니다. 이를 통해 개발자는 MIDI 입력을 수신하고, MIDI 메시지를 처리하여 음악 ...
Meta Keywords: midi, input, inputs, function, midiinput
-->

# MIDIInput: 자바스크립트에서 MIDI 장치와의 상호작용

## 개요
MIDIInput은 웹 오디오 API의 일부분으로, 브라우저에서 MIDI 장치와의 상호작용을 가능하게 해줍니다. 이를 통해 개발자는 MIDI 입력을 수신하고, MIDI 메시지를 처리하여 음악 애플리케이션이나 게임 등을 구현할 수 있습니다.

## 문서화

### 목적
MIDIInput 인터페이스는 MIDI 장치로부터 입력되는 데이터를 처리하기 위해 설계되었습니다. 이를 통해 사용자는 MIDI 키보드, 컨트롤러 등의 장치에서 발생하는 이벤트를 쉽게 수신할 수 있습니다.

### 사용법
MIDIInput 객체는 Web MIDI API를 통해 생성됩니다. 사용자는 `navigator.requestMIDIAccess()` 메서드를 호출하여 MIDI 장치에 접근한 후, `inputs` 프로퍼티에서 MIDIInput 객체를 얻을 수 있습니다.

### 세부사항
- **속성**: 
  - `state`: MIDIInput의 상태를 나타내며, "disconnected" 또는 "connected" 값 중 하나를 가집니다.
  
- **메서드**:
  - `addEventListener(type, listener)`: 지정한 유형의 이벤트가 발생할 때 호출될 리스너를 추가합니다.
  - `removeEventListener(type, listener)`: 추가된 리스너를 제거합니다.

- **이벤트**:
  - `midimessage`: MIDI 메시지가 수신될 때 발생합니다.

## 예제

### 기본 사용 예제
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(function(input) {
        input.addEventListener('midimessage', function(event) {
            console.log('MIDI message received:', event.data);
        });
    });
});
```

### 특정 MIDIInput에서 메시지 수신
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const input = midiAccess.inputs.get('YOUR_MIDI_INPUT_ID');
    if (input) {
        input.addEventListener('midimessage', function(event) {
            console.log('MIDI message from specific input:', event.data);
        });
    }
});
```

## 설명

### 일반적인 함정 및 추가 노트
- **브라우저 호환성**: 모든 브라우저가 MIDI API를 지원하지 않으므로, 사용 전에 호환성을 확인해야 합니다.
- **MIDI 장치 연결**: MIDI 장치가 연결되어 있지 않으면 이벤트를 받을 수 없습니다. 따라서, 사용자는 MIDI 장치 상태를 점검해야 합니다.
- **비동기 처리**: `requestMIDIAccess()`는 비동기 메서드로, Promise를 반환하므로 `.then()` 또는 `async/await` 구문을 사용하여 결과를 처리해야 합니다.

## 한 문장 요약
MIDIInput은 자바스크립트를 통해 웹에서 MIDI 장치의 입력을 처리할 수 있도록 해주는 인터페이스입니다.