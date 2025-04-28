<!--
Meta Description: # RTCPeerConnection: JavaScript를 활용한 WebRTC의 핵심 컴포넌트 ## 개요 RTCPeerConnection은 WebRTC(웹 실시간 통신) API의 핵심 구성 요소로, 브라우저 간의 오디오, 비디오 및 데이터 전송을 가능하게 합니다. 이 ...
Meta Keywords: 합니다, peerconnection, ice, rtcpeerconnection, 미디어
-->

# RTCPeerConnection: JavaScript를 활용한 WebRTC의 핵심 컴포넌트

## 개요
RTCPeerConnection은 WebRTC(웹 실시간 통신) API의 핵심 구성 요소로, 브라우저 간의 오디오, 비디오 및 데이터 전송을 가능하게 합니다. 이 객체는 P2P(피어 투 피어) 연결을 관리하고, 미디어 스트림을 송수신하며, 보안성을 제공합니다.

## 문서화

### 목적
RTCPeerConnection은 두 개의 웹 브라우저 간에 실시간으로 미디어 및 데이터를 전송하기 위한 안정적이고 효율적인 연결을 설정하는 것을 목적으로 합니다. 이 객체는 ICE(Interactive Connectivity Establishment) 프로토콜을 사용하여 NAT(네트워크 주소 변환)와 방화벽을 통과할 수 있도록 합니다.

### 사용법
RTCPeerConnection을 사용하려면 먼저 객체를 생성한 후, ICE 후보를 수집하고, 세션 설명을 설정하여 연결을 구성해야 합니다.

```javascript
// RTCPeerConnection 객체 생성
const peerConnection = new RTCPeerConnection(configuration);

// ICE 후보 수집 이벤트 처리
peerConnection.onicecandidate = event => {
    if (event.candidate) {
        // 후보를 다른 피어에게 전송
        sendCandidateToRemotePeer(event.candidate);
    }
};

// 스트림 추가
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    });
```

### 세부 사항
- **configuration**: RTCPeerConnection 생성자는 ICE 서버에 대한 설정을 포함하는 객체를 인자로 받습니다. 예를 들어, STUN 및 TURN 서버 정보를 포함할 수 있습니다.
- **addIceCandidate**: 원격 피어로부터 수신한 ICE 후보를 추가하는 메서드입니다.
- **createOffer / createAnswer**: 피어 간의 연결을 설정하기 위해 제안 및 응답을 생성하는 메서드입니다.
- **setLocalDescription / setRemoteDescription**: 로컬 및 원격 세션 설명을 설정하여 연결을 구성합니다.

## 예제
### 기본 사용 예제
아래는 간단한 RTCPeerConnection 사용 예제입니다.

```javascript
const configuration = {
    iceServers: [
        { urls: 'stun:stun.l.google.com:19302' }
    ]
};

const peerConnection = new RTCPeerConnection(configuration);

// 로컬 미디어 스트림 추가
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    });

// 제안 생성 및 전송
peerConnection.createOffer()
    .then(offer => {
        return peerConnection.setLocalDescription(offer);
    })
    .then(() => {
        // 로컬 제안을 원격 피어에 전송
        sendOfferToRemotePeer(peerConnection.localDescription);
    });
```

## 설명
### 일반적인 실수 및 주의 사항
- **ICE 후보 처리**: ICE 후보를 적절하게 처리하지 않으면 연결이 실패할 수 있습니다. 항상 onicecandidate 이벤트를 통해 후보를 수집하고 전달해야 합니다.
- **미디어 스트림 관리**: 미디어 스트림을 추가할 때, 올바른 트랙을 사용하고 있는지 확인해야 합니다. 특히, 비디오와 오디오 트랙을 혼동하지 않도록 주의해야 합니다.
- **에러 처리**: RTCPeerConnection의 메서드는 프로미스를 반환하므로, 항상 에러를 처리할 수 있는 로직을 포함해야 합니다.

## 한 문장 요약
RTCPeerConnection은 JavaScript에서 WebRTC를 통해 브라우저 간 실시간 미디어 및 데이터 통신을 가능하게 하는 객체입니다.