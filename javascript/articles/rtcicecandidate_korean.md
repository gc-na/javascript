<!--
Meta Description: # RTCIceCandidate: JavaScript에서의 웹RTC 후보자 ## 개요 RTCIceCandidate는 웹RTC(Web Real-Time Communication) API의 구성 요소로, 네트워크 연결을 수립하기 위해 ICE(Interactive Conne...
Meta Keywords: rtcicecandidate, ice, candidate, 네트워크, 연결을
-->

# RTCIceCandidate: JavaScript에서의 웹RTC 후보자

## 개요
RTCIceCandidate는 웹RTC(Web Real-Time Communication) API의 구성 요소로, 네트워크 연결을 수립하기 위해 ICE(Interactive Connectivity Establishment) 프로토콜을 사용하여 후보 네트워크 경로를 나타냅니다. 이 객체는 P2P(피어 투 피어) 통신에서 최적의 연결을 설정하는 데 중요한 역할을 합니다.

## 문서화
### 목적
RTCIceCandidate 객체는 웹RTC 애플리케이션에서 피어 간의 연결을 설정하기 위한 후보 정보를 담고 있습니다. 이 객체는 후보의 주소, 포트, 프로토콜 및 우선순위를 포함하고 있어, 클라이언트 간의 최적 경로를 선택하는 데 필수적입니다.

### 사용법
RTCIceCandidate 객체는 주로 `RTCPeerConnection`의 `addIceCandidate()` 메서드와 함께 사용됩니다. 후보가 성공적으로 추가되면, 연결이 가능한 네트워크 경로가 형성됩니다.

#### 생성자
```javascript
let candidate = new RTCIceCandidate({
  candidate: "candidate:123456789 1 udp 2122260223 192.168.1.1 5678 typ host",
  sdpMid: "0",
  sdpMLineIndex: 0
});
```

#### 주요 프로퍼티
- `candidate`: ICE 후보를 나타내는 문자열.
- `sdpMid`: 후보가 속한 미디어의 식별자.
- `sdpMLineIndex`: SDP에서의 미디어 라인의 인덱스.

## 예제
### 기본 사용 예제
```javascript
// RTCIceCandidate 객체 생성
const iceCandidate = new RTCIceCandidate({
  candidate: "candidate:1 1 udp 2122260223 192.168.1.1 5678 typ host",
  sdpMid: "audio",
  sdpMLineIndex: 0
});

// RTCPeerConnection에 ICE 후보 추가
const peerConnection = new RTCPeerConnection();
peerConnection.addIceCandidate(iceCandidate)
  .then(() => {
    console.log("ICE 후보가 성공적으로 추가되었습니다.");
  })
  .catch(error => {
    console.error("ICE 후보 추가 실패:", error);
  });
```

## 설명
RTCIceCandidate를 사용할 때 몇 가지 주의해야 할 점이 있습니다:
- ICE 후보는 특정 네트워크 조건에 따라 다를 수 있으므로, 후보가 유효한지 확인해야 합니다.
- `addIceCandidate()` 메서드는 비동기적으로 작동하므로, 성공적으로 추가되었는지 확인하기 위해 프로미스를 처리해야 합니다.
- 후보는 오프라인 상태에서 생성할 수 있지만, 실제 연결을 위해서는 네트워크가 필요합니다.

## 한 줄 요약
RTCIceCandidate는 웹RTC에서 P2P 통신을 위한 네트워크 후보 정보를 제공하는 객체입니다.