<!--
Meta Description: # RTCSessionDescription: JavaScript에서의 WebRTC 세션 설명 ## 개요 `RTCSessionDescription`은 WebRTC API의 일부로, 오디오 및 비디오 스트림을 전송하기 위한 세션의 속성을 정의합니다. 이 객체는 SDP(Se...
Meta Keywords: sdp, rtcsessiondescription, offer, answer, error
-->

# RTCSessionDescription: JavaScript에서의 WebRTC 세션 설명

## 개요
`RTCSessionDescription`은 WebRTC API의 일부로, 오디오 및 비디오 스트림을 전송하기 위한 세션의 속성을 정의합니다. 이 객체는 SDP(Session Description Protocol) 정보를 포함하여 피어 간의 연결 설정에 필요한 정보를 제공합니다.

## 문서화
`RTCSessionDescription` 객체는 WebRTC 연결을 설정하는 데 필요한 세션 설명을 나타냅니다. 이 객체는 일반적으로 두 가지 주요 파라미터인 `type`과 `sdp`를 포함합니다:

- **type**: 세션 설명의 유형을 나타내며, `offer` 또는 `answer` 중 하나입니다. `offer`는 세션을 시작하려는 피어가 제공하는 설명이고, `answer`는 해당 설명에 대한 응답입니다.
- **sdp**: 세션의 상세 정보를 포함하는 문자열로, 오디오 및 비디오 코덱, 네트워크 정보 등을 담고 있습니다.

### 사용법
`RTCSessionDescription` 객체는 새로운 인스턴스를 생성하는 방식으로 사용됩니다. JavaScript에서 이를 생성하는 방법은 다음과 같습니다:

```javascript
let offer = new RTCSessionDescription({
    type: 'offer',
    sdp: 'v=0\r\n...' // SDP 내용
});
```

이 예제는 WebRTC 연결을 위한 오퍼 세션 설명을 생성합니다. 주의할 점은 SDP 문자열이 유효한 형식을 가져야 한다는 것입니다.

## 예제
### 기본 사용 예제
```javascript
// RTCSessionDescription 객체 생성
const offer = new RTCSessionDescription({
    type: 'offer',
    sdp: 'v=0\r\n...' // 유효한 SDP 문자열
});

// RTCConnection 객체에 오퍼 설정
peerConnection.setLocalDescription(offer)
    .then(() => {
        console.log('로컬 설명이 설정되었습니다:', offer);
    })
    .catch(error => {
        console.error('설정 중 오류 발생:', error);
    });
```

### 응답 처리 예제
```javascript
// 피어가 받은 응답을 RTCSessionDescription으로 설정
const answer = new RTCSessionDescription({
    type: 'answer',
    sdp: 'v=0\r\n...' // 유효한 SDP 문자열
});

peerConnection.setRemoteDescription(answer)
    .then(() => {
        console.log('원격 설명이 설정되었습니다:', answer);
    })
    .catch(error => {
        console.error('설정 중 오류 발생:', error);
    });
```

## 설명
`RTCSessionDescription`을 사용할 때 몇 가지 일반적인 주의 사항이 있습니다:

- **SDP 형식**: SDP는 특정 형식을 따라야 하며, 유효하지 않은 SDP 문자열을 사용하면 연결 오류가 발생할 수 있습니다.
- **비동기 처리**: `setLocalDescription` 및 `setRemoteDescription` 메서드는 비동기적으로 작동하므로, 결과를 처리할 때는 `Promise`를 사용하여 오류를 적절히 처리해야 합니다.
- **ICE 후보**: `RTCSessionDescription`은 ICE 후보와 함께 사용되어야 하며, 이를 통해 NAT를 통과하여 피어 간에 연결을 설정할 수 있습니다.

## 한 줄 요약
`RTCSessionDescription`은 WebRTC에서 오디오 및 비디오 세션의 속성을 정의하는 객체로, 세션 설명을 통해 피어 간의 연결을 설정합니다.