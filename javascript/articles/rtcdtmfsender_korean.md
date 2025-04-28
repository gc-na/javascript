<!--
Meta Description: # RTCDTMFSender: JavaScript에서 DTMF 신호 전송하기 ## 개요 RTCDTMFSender는 WebRTC API의 일부로, 실시간 통신에서 DTMF(Dual-tone multi-frequency) 신호를 전송하는 기능을 제공합니다. 이 기능은 Vo...
Meta Keywords: dtmf, 신호를, rtcdtmfsender, 전송할, 전송하는
-->

# RTCDTMFSender: JavaScript에서 DTMF 신호 전송하기

## 개요
RTCDTMFSender는 WebRTC API의 일부로, 실시간 통신에서 DTMF(Dual-tone multi-frequency) 신호를 전송하는 기능을 제공합니다. 이 기능은 VoIP(Voice over IP) 애플리케이션에서 전화 키패드 입력을 처리하는 데 유용합니다.

## 문서화
### 목적
RTCDTMFSender 객체는 WebRTC 연결을 통해 DTMF 신호를 전송할 수 있는 방법을 제공합니다. 이를 통해 사용자는 전화 통화 중에 숫자, 기호 및 기타 문자를 전송할 수 있습니다.

### 사용법
RTCDTMFSender 객체는 RTCPeerConnection 객체에 의해 생성됩니다. DTMF 신호를 전송하려면 먼저 RTCPeerConnection을 설정한 후, `createDTMFSender` 메서드를 호출하여 RTCDTMFSender 인스턴스를 생성합니다.

### 세부사항
- **메서드**
  - `insertDTMF(tones, duration, interToneGap)`: DTMF 신호를 전송하는 메서드입니다.
    - `tones`: 전송할 DTMF 톤의 문자열입니다. (예: "123#")
    - `duration`: 각 톤의 지속 시간 (밀리초 단위, 기본값은 100ms)
    - `interToneGap`: 톤 사이의 간격 (밀리초 단위, 기본값은 70ms)
  
### 생성 예시
```javascript
// RTCPeerConnection 생성
const peerConnection = new RTCPeerConnection(config);

// DTMF 송신기 생성
const dtmfSender = peerConnection.createDTMFSender(track);

// DTMF 신호 전송
dtmfSender.insertDTMF("123#");
```

## 설명
- **일반적인 문제**
  - DTMF 신호가 전송되지 않는 경우: RTCPeerConnection이 제대로 설정되었는지 확인하세요. 연결이 이루어지지 않으면 DTMF 신호를 전송할 수 없습니다.
  - 톤 지속 시간과 간격이 너무 짧거나 길 경우, 수신 측에서 신호를 인식하지 못할 수 있습니다. 적절한 값을 설정하는 것이 중요합니다.

- **추가 노트**
  - DTMF 신호는 음성 통화 중에 다양한 기능(예: 자동 응답 시스템)과 상호작용하는 데 필요합니다.
  - 브라우저 호환성에 유의해야 합니다. 최신 브라우저에서 대부분 지원하지만, 특정 기능은 제한적일 수 있습니다.

## 한 줄 요약
RTCDTMFSender는 WebRTC를 통해 DTMF 신호를 전송하는 JavaScript API입니다.