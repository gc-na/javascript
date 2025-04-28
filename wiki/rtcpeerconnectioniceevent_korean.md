<!--
Meta Description: # RTCPeerConnectionIceEvent: JavaScript에서의 WebRTC ICE 이벤트 이해하기 ## 개요 `RTCPeerConnectionIceEvent`는 WebRTC API에서 ICE(Interactive Connectivity Establishm...
Meta Keywords: ice, rtcpeerconnectioniceevent, candidate, rtcpeerconnection, 이벤트
-->

# RTCPeerConnectionIceEvent: JavaScript에서의 WebRTC ICE 이벤트 이해하기

## 개요
`RTCPeerConnectionIceEvent`는 WebRTC API에서 ICE(Interactive Connectivity Establishment) 프로세스와 관련된 이벤트로, Peer-to-Peer 연결을 위한 중요한 요소입니다. 이 이벤트는 ICE candidate가 발견되거나 연결 상태가 변경될 때 발생합니다.

## 문서화
`RTCPeerConnectionIceEvent`는 WebRTC의 `RTCPeerConnection` 객체에서 발생하는 이벤트로, ICE candidate에 대한 정보를 제공합니다. 이 이벤트는 주로 네트워크 설정과 연결 상태를 관리하는 데 사용됩니다.

### 목적
`RTCPeerConnectionIceEvent`는 ICE candidate가 추가될 때, 또는 ICE 연결 상태가 변화할 때 애플리케이션에 알림을 제공합니다. 이를 통해 개발자는 최적의 네트워크 경로를 선택하고 연결을 안정적으로 유지할 수 있습니다.

### 사용법
`RTCPeerConnectionIceEvent`는 `RTCPeerConnection` 객체의 `icecandidate` 이벤트 리스너를 통해 사용됩니다. 이벤트 객체는 추가된 ICE candidate에 대한 정보를 포함하고 있습니다.

### 세부사항
- **event.candidate**: 새로운 ICE candidate 정보를 포함하는 `RTCIceCandidate` 객체입니다.
- 이벤트는 `RTCPeerConnection` 객체가 ICE candidate를 발견할 때마다 발생합니다.
- 이 이벤트는 네트워크 연결의 성능을 최적화하기 위해 실시간으로 처리해야 합니다.

## 예제
다음은 `RTCPeerConnectionIceEvent`를 사용하는 기본적인 예제입니다.

```javascript
// RTCPeerConnection 객체 생성
const peerConnection = new RTCPeerConnection();

// ICE candidate가 추가될 때 이벤트 리스너 등록
peerConnection.addEventListener('icecandidate', (event) => {
    if (event.candidate) {
        console.log('새로운 ICE candidate:', event.candidate);
        // 여기서 candidate를 신호 서버에 전송하거나 처리할 수 있습니다.
    }
});

// ICE candidate 추가를 위한 연결 설정
async function createOffer() {
    const offer = await peerConnection.createOffer();
    await peerConnection.setLocalDescription(offer);
    // 신호 서버에 offer를 전송
}
```

## 설명
`RTCPeerConnectionIceEvent`를 사용할 때 주의할 점은 다음과 같습니다:
- ICE candidate를 수집하는 동안 연결이 불안정할 수 있으므로, 이벤트가 발생할 때마다 적절하게 처리해야 합니다.
- 네트워크 환경에 따라 candidate가 수집되는 속도가 다를 수 있으며, 이로 인해 연결 지연이 발생할 수 있습니다.
- candidate를 신호 서버에 전송할 때, 적절한 포맷으로 전송해야 하며, 신호 서버와의 통신이 원활해야 합니다.

## 요약
`RTCPeerConnectionIceEvent`는 WebRTC에서 ICE candidate의 추가 및 변경을 처리하는 데 중요한 역할을 하며, P2P 연결을 최적화하는 데 필수적입니다.