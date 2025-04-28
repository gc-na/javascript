<!--
Meta Description: # RTCPeerConnectionIceErrorEvent: JavaScript WebRTC의 ICE 오류 이벤트 ## 개요 `RTCPeerConnectionIceErrorEvent`는 WebRTC API에서 ICE(Interactive Connectivity Esta...
Meta Keywords: ice, rtcpeerconnectioniceerrorevent, event, 이벤트는, peerconnection
-->

# RTCPeerConnectionIceErrorEvent: JavaScript WebRTC의 ICE 오류 이벤트

## 개요
`RTCPeerConnectionIceErrorEvent`는 WebRTC API에서 ICE(Interactive Connectivity Establishment) 오류와 관련된 이벤트입니다. 이 이벤트는 ICE 후보가 잘못되었거나 연결 문제로 인해 ICE 프로세스가 실패할 때 발생합니다. WebRTC에서 실시간 통신을 구현할 때, 이 오류 이벤트는 연결 상태를 모니터링하는 데 필수적입니다.

## 문서화

### 목적
`RTCPeerConnectionIceErrorEvent`는 WebRTC 연결 중 발생하는 ICE 오류를 식별하고 처리할 수 있도록 돕습니다. 이 이벤트는 개발자가 실시간 통신에서의 연결 문제를 감지하고 적절한 조치를 취할 수 있게 해줍니다.

### 사용법
`RTCPeerConnectionIceErrorEvent`는 `RTCPeerConnection` 객체의 `iceerror` 이벤트로 발생합니다. 이 이벤트는 ICE 오류가 발생했을 때 자동으로 트리거되며, 관련된 오류 정보를 포함합니다.

이벤트는 아래와 같은 속성을 가집니다:
- `errorCode`: 오류의 코드값.
- `hostCandidate`: 오류가 발생한 후보의 정보.
- `url`: 관련된 ICE 서버의 URL.

### 이벤트 리스너 등록 예시
```javascript
const peerConnection = new RTCPeerConnection();

// ICE 오류 이벤트 리스너 등록
peerConnection.addEventListener('iceerror', (event) => {
    console.error(`ICE 오류 발생: ${event.errorCode}`);
    console.error(`오류 발생 후보: ${event.hostCandidate}`);
    console.error(`관련 ICE 서버 URL: ${event.url}`);
});
```

## 예제
간단한 RTCPeerConnection을 설정하고 ICE 오류 이벤트를 처리하는 기본 예제입니다.

```javascript
const peerConnection = new RTCPeerConnection();

// ICE 오류 이벤트 리스너 등록
peerConnection.addEventListener('iceerror', (event) => {
    console.log(`ICE 오류 발생: ${event.errorCode}`);
});

// 가상의 ICE 후보 추가 (실제로는 적절한 후보를 추가해야 함)
peerConnection.addIceCandidate(new RTCIceCandidate({
    candidate: 'candidate-string',
    sdpMid: 'audio',
    sdpMLineIndex: 0
}));
```

## 설명
`RTCPeerConnectionIceErrorEvent`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **정확한 오류 코드 파악**: `errorCode`는 오류의 원인을 이해하는 데 중요한 정보입니다. 이를 통해 어떤 문제가 발생했는지 파악할 수 있습니다.
- **후보 정보 확인**: `hostCandidate` 속성은 문제가 발생한 후보의 정보를 제공합니다. 이 정보를 통해 후보의 유효성을 검사할 수 있습니다.
- **ICE 서버 설정**: ICE 오류는 서버 설정이나 네트워크 문제로 인해 발생할 수 있습니다. 올바른 STUN/TURN 서버를 설정하는 것이 중요합니다.

## 한 줄 요약
`RTCPeerConnectionIceErrorEvent`는 WebRTC에서 ICE 오류를 감지하고 처리할 수 있는 이벤트로, 실시간 통신의 안정성을 높이는 데 필수적입니다.