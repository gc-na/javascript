<!--
Meta Description: # RTCDTMFToneChangeEvent: 자바스크립트에서의 DTMF 톤 변경 이벤트 ## 개요 RTCDTMFToneChangeEvent는 WebRTC API에서 사용되는 이벤트로, DTMF(Dual-tone multi-frequency) 톤이 변경될 때 발생합니다...
Meta Keywords: dtmf, 이벤트, rtcdtmftonechangeevent는, tone, 변화를
-->

# RTCDTMFToneChangeEvent: 자바스크립트에서의 DTMF 톤 변경 이벤트

## 개요
RTCDTMFToneChangeEvent는 WebRTC API에서 사용되는 이벤트로, DTMF(Dual-tone multi-frequency) 톤이 변경될 때 발생합니다. 이 이벤트는 전화 통화 중 톤 신호를 전송할 때 유용하게 활용됩니다.

## 문서화
RTCDTMFToneChangeEvent는 WebRTC에서 DTMF 신호의 변화를 모니터링하는 데 사용됩니다. 이 이벤트는 DTMF 전송을 관리하는 RTCDtmfSender 인터페이스와 함께 작동하며, DTMF 톤이 생성되거나 중지될 때마다 발행됩니다. 

### 목적
- DTMF 톤의 실시간 변화를 감지하고 처리하기 위함입니다.
  
### 사용법
RTCDTMFToneChangeEvent는 `RTCDtmfSender` 객체에 의해 발생하며, 이 객체의 `ontonechange` 핸들러를 사용하여 이벤트를 수신할 수 있습니다. 

### 속성
- `tone`: 변경된 DTMF 톤을 나타내는 문자(예: '0', '1', 'A', 'B', 'C', 'D', '#', '*').
- `timeStamp`: 이벤트가 발생한 시간을 나타내는 타임스탬프.

## 예제
아래는 RTCDTMFToneChangeEvent를 사용하는 기본적인 예제입니다.

```javascript
// RTCPeerConnection 생성
const peerConnection = new RTCPeerConnection();

// DTMF 송신기 생성
const dtmfSender = peerConnection.createDTMFSender(yourMediaStreamTrack);

// DTMF 톤 변경 이벤트 리스너 추가
dtmfSender.ontonechange = (event) => {
    console.log('DTMF 톤이 변경되었습니다:', event.tone);
};

// DTMF 톤 전송
dtmfSender.insertDTMF('5');
```

## 설명
RTCDTMFToneChangeEvent를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **브라우저 호환성**: WebRTC API는 모든 브라우저에서 동일하게 지원되지 않을 수 있으므로, 사용하기 전에 호환성을 확인해야 합니다.
2. **상태 관리**: DTMF 톤을 전송하는 동안 이벤트 핸들러 내에서 상태를 적절히 관리해야 합니다. 이벤트가 발생할 때마다 현재 상태를 동기화하지 않으면 예상치 못한 결과가 발생할 수 있습니다.
3. **이벤트 수신**: DTMF 톤이 변경될 때마다 이벤트가 발생하므로, 너무 많은 이벤트를 처리하지 않도록 주의해야 합니다.

## 한 줄 요약
RTCDTMFToneChangeEvent는 WebRTC에서 DTMF 톤의 변화를 감지하고 처리하는 데 사용되는 이벤트입니다.