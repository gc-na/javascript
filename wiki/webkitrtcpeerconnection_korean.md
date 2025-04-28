<!--
Meta Description: # webkitRTCPeerConnection: 웹RTC를 활용한 실시간 통신을 위한 JavaScript API ## 개요 `webkitRTCPeerConnection`은 WebRTC API의 일부로, 웹 애플리케이션에서 실시간 오디오 및 비디오 통신을 가능하게 하는 ...
Meta Keywords: webkitrtcpeerconnection, peerconnection, ice, const, event
-->

# webkitRTCPeerConnection: 웹RTC를 활용한 실시간 통신을 위한 JavaScript API

## 개요
`webkitRTCPeerConnection`은 WebRTC API의 일부로, 웹 애플리케이션에서 실시간 오디오 및 비디오 통신을 가능하게 하는 객체입니다. 이 API는 브라우저 간의 P2P 연결을 설정하고 관리하는 데 사용됩니다.

## 문서화
### 목적
`webkitRTCPeerConnection`은 웹 브라우저에서 다른 브라우저와 직접 연결하여 오디오 및 비디오 스트리밍을 가능하게 합니다. 이는 화상 회의, 파일 전송, 게임 등 다양한 애플리케이션에서 활용됩니다.

### 사용법
`webkitRTCPeerConnection`은 WebRTC의 Peer-to-Peer 연결을 설정하기 위해 생성됩니다. 다음은 기본적인 사용법입니다.

```javascript
const configuration = {
  iceServers: [
    { urls: 'stun:stun.l.google.com:19302' }
  ]
};

const peerConnection = new webkitRTCPeerConnection(configuration);
```

여기서 `iceServers`는 ICE 후보를 찾기 위해 사용할 서버의 목록을 정의합니다.

### 세부사항
- **생성자**: `new webkitRTCPeerConnection(configuration)`을 통해 새로운 PeerConnection 인스턴스를 생성합니다.
- **메서드**:
  - `createOffer()`: 원격 피어에 연결하기 위한 세션 설명을 생성합니다.
  - `createAnswer()`: 수신된 Offer에 대한 응답을 생성합니다.
  - `setLocalDescription()`: 로컬 세션 설명을 설정합니다.
  - `setRemoteDescription()`: 원격 세션 설명을 설정합니다.
- **이벤트**:
  - `onicecandidate`: ICE 후보가 발견될 때 발생합니다.
  - `ontrack`: 원격 트랙이 추가될 때 발생합니다.

## 예제
### 기본 사용 예제
```javascript
const peerConnection = new webkitRTCPeerConnection(configuration);

// ICE 후보 수집 이벤트 핸들러
peerConnection.onicecandidate = (event) => {
  if (event.candidate) {
    console.log('ICE Candidate:', event.candidate);
  }
};

// 원격 트랙 수신 이벤트 핸들러
peerConnection.ontrack = (event) => {
  const remoteStream = event.streams[0];
  const videoElement = document.getElementById('remoteVideo');
  videoElement.srcObject = remoteStream;
};

// Offer 생성 및 전송
peerConnection.createOffer()
  .then(offer => peerConnection.setLocalDescription(offer))
  .then(() => {
    // Offer를 상대방에게 전송하는 코드 필요
  });
```

## 설명
`webkitRTCPeerConnection`을 사용할 때 주의해야 할 점은 다음과 같습니다:
- **브라우저 호환성**: `webkitRTCPeerConnection`은 Safari와 같은 웹킷 기반 브라우저에서 사용됩니다. 다른 브라우저에서는 `RTCPeerConnection`을 사용해야 합니다.
- **ICE 후보**: 연결이 성공적으로 이루어지기 위해서는 ICE 후보가 수집되고 교환되어야 합니다. 따라서 네트워크 설정과 ICE 서버의 설정이 중요합니다.
- **보안**: WebRTC는 기본적으로 보안 연결을 요구하므로 HTTPS 환경에서 사용해야 합니다.

## 한 줄 요약
`webkitRTCPeerConnection`은 웹 애플리케이션에서 실시간 오디오 및 비디오 통신을 가능하게 하는 WebRTC API의 핵심 구성 요소입니다.