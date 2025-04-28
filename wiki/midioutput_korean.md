<!--
Meta Description: # MIDIOutput: JavaScript에서 MIDI 신호 출력하기 ## 개요 MIDIOutput는 JavaScript를 사용하여 MIDI 장치에 신호를 출력하는 기능을 제공합니다. 이 기능은 웹 기반 음악 애플리케이션 및 게임에서 MIDI 데이터를 송신하는 데 유...
Meta Keywords: midi, outputs, 합니다, output, 장치에
-->

# MIDIOutput: JavaScript에서 MIDI 신호 출력하기

## 개요
MIDIOutput는 JavaScript를 사용하여 MIDI 장치에 신호를 출력하는 기능을 제공합니다. 이 기능은 웹 기반 음악 애플리케이션 및 게임에서 MIDI 데이터를 송신하는 데 유용합니다.

## 문서
### 목적
MIDIOutput는 웹 MIDI API의 일부로, 사용자에게 MIDI 장치와의 상호작용을 가능하게 하여 음악 프로그래밍 및 실시간 오디오 처리에서 중요한 역할을 합니다.

### 사용법
MIDIOutput를 사용하려면 먼저 웹 MIDI API를 활성화해야 합니다. 사용자는 `navigator.requestMIDIAccess()` 메서드를 호출하여 MIDI 장치에 접근하고, 이후 MIDIOutput 객체를 통해 MIDI 신호를 송신할 수 있습니다.

#### 기본 문법
```javascript
navigator.requestMIDIAccess().then(successCallback, errorCallback);
```

#### 성공 콜백
성공적인 MIDI 접근 후, MIDIOutput 객체를 얻기 위해 다음과 같은 절차를 따릅니다.

```javascript
function successCallback(midiAccess) {
    const outputs = midiAccess.outputs;
    outputs.forEach(output => {
        // MIDI 신호 전송
        output.send([0x90, 60, 0x7f]); // 노트 온 메시지
    });
}
```

### 예제
```javascript
navigator.requestMIDIAccess().then(midiAccess => {
    const outputs = midiAccess.outputs;
    if (outputs.size > 0) {
        const output = outputs.values().next().value;
        // C4 노트 온 메시지 전송
        output.send([0x90, 60, 0x7f]); // 노트 온
        output.send([0x80, 60, 0x40]); // 노트 오프
    }
}, error => {
    console.error('MIDI 접근 실패:', error);
});
```

### 설명
MIDIOutput을 사용할 때 주의해야 할 점은 다음과 같습니다:

- **브라우저 호환성**: 모든 브라우저가 MIDI API를 지원하지 않으므로, 기능 사용 전에 호환성을 확인해야 합니다.
- **사용자 허가**: MIDI 장치에 접근하려면 사용자의 허가가 필요합니다. 따라서, 코드 실행 시 사용자가 허가 대화상자를 수락해야 합니다.
- **메시지 형식**: MIDI 메시지는 배열 형식으로 전송되며, 메시지 유형(예: 노트 온, 노트 오프)과 파라미터가 올바르게 설정되어야 합니다.
- **출력 장치 선택**: 여러 MIDI 출력 장치가 연결된 경우, 원하는 장치를 명시적으로 선택해야 할 수 있습니다.

## 한 줄 요약
MIDIOutput는 JavaScript에서 MIDI 장치에 신호를 송신하여 음악 애플리케이션을 개발하는 데 필요한 기능입니다.