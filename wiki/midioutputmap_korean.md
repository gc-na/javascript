<!--
Meta Description: # MIDIOutputMap: 자바스크립트에서 MIDI 출력 장치 관리하기 ## 개요 MIDIOutputMap은 웹 MIDI API의 일부로, 자바스크립트에서 MIDI 출력 장치에 대한 정보를 제공하는 객체입니다. 이 객체를 통해 개발자는 웹 애플리케이션에서 MIDI ...
Meta Keywords: midi, outputs, 있습니다, 장치에, output
-->

# MIDIOutputMap: 자바스크립트에서 MIDI 출력 장치 관리하기

## 개요
MIDIOutputMap은 웹 MIDI API의 일부로, 자바스크립트에서 MIDI 출력 장치에 대한 정보를 제공하는 객체입니다. 이 객체를 통해 개발자는 웹 애플리케이션에서 MIDI 신호를 전송할 수 있는 다양한 장치들을 효율적으로 관리할 수 있습니다.

## 문서화

### 목적
MIDIOutputMap은 현재 연결된 MIDI 출력 장치의 정보를 포함한 객체로, 각 장치의 이름, ID, 상태 등을 제공합니다. 이를 통해 개발자는 특정 MIDI 장치에 대한 명확한 접근과 제어를 할 수 있습니다.

### 사용법
MIDIOutputMap은 `navigator.requestMIDIAccess()` 함수를 통해 MIDI 장치에 접근한 후 얻을 수 있습니다. 이 함수는 프로미스를 반환하며, 성공적으로 MIDI 액세스가 허용되면 `outputs` 프로퍼티를 통해 MIDIOutputMap을 이용할 수 있습니다.

#### 기본 구조
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs; // MIDIOutputMap
    // MIDI 출력 장치에 대한 작업 수행
});
```

### 세부 정보
- **형식**: MIDIOutputMap은 `Map` 객체로, 각 MIDI 출력 장치의 ID를 키로 하고, 해당 장치의 `MIDIOutput` 객체를 값으로 가집니다.
- **MIDIOutput 객체**: 각 출력 장치는 `send()` 메서드를 사용하여 MIDI 메시지를 전송할 수 있습니다. 추가적으로, `name`, `id`와 같은 장치에 대한 정보도 포함되어 있습니다.

## 예제
### 기본 사용 예제
다음은 MIDI 출력 장치 목록을 가져와서 각 장치의 이름을 콘솔에 출력하는 예제입니다.

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    outputs.forEach(output => {
        console.log(`장치 이름: ${output.name}, ID: ${output.id}`);
    });
});
```

### MIDI 메시지 전송 예제
MIDI 출력 장치에 신호를 전송하는 예제입니다.

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    const output = outputs.get('output-device-id'); // 실제 장치 ID 사용
    if (output) {
        const noteOnMessage = [0x90, 60, 0x7f]; // 노트 온 메시지
        output.send(noteOnMessage); // 메시지 전송
    }
});
```

## 설명
- **일반적인 함정**: MIDI 장치가 연결되어 있지 않거나, 사용자가 MIDI 액세스를 허용하지 않는 경우, `requestMIDIAccess()`가 실패할 수 있습니다. 이 경우, 적절한 오류 처리가 필요합니다.
- **비동기 처리**: MIDI 장치에 대한 접근은 비동기적으로 이루어지므로, 프로미스를 적절히 처리해야 합니다. `.then()`과 `.catch()`를 사용하여 성공 및 실패 시나리오를 처리할 수 있습니다.
- **버전 호환성**: MIDIOutputMap은 최신 브라우저에서 지원되지만, 일부 구형 브라우저에서는 지원되지 않을 수 있으므로, 브라우저 호환성 확인이 필요합니다.

## 한 줄 요약
MIDIOutputMap은 웹 MIDI API를 통해 자바스크립트에서 MIDI 출력 장치를 관리하고 제어하는 데 사용되는 객체입니다.