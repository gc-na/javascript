<!--
Meta Description: # RTCRtpSender: JavaScript에서 실시간 통신을 위한 RTP 전송 기능 ## 개요 RTCRtpSender는 WebRTC API의 일부로, 실시간 통신에서 미디어 스트림을 전송할 때 사용됩니다. 이 객체는 오디오 및 비디오 트랙을 원격 피어에 전송하며,...
Meta Keywords: 트랙을, track, rtcrtpsender는, stream, 미디어
-->

# RTCRtpSender: JavaScript에서 실시간 통신을 위한 RTP 전송 기능

## 개요
RTCRtpSender는 WebRTC API의 일부로, 실시간 통신에서 미디어 스트림을 전송할 때 사용됩니다. 이 객체는 오디오 및 비디오 트랙을 원격 피어에 전송하며, 다양한 설정을 통해 전송 품질을 조절할 수 있습니다.

## 문서화
### 목적
RTCRtpSender는 WebRTC에서 미디어 트랙을 전송하는 데 필요한 기능을 제공합니다. 이 객체는 트랙의 상태를 모니터링하고, 전송에 필요한 다양한 매개변수를 설정할 수 있도록 지원합니다.

### 사용법
RTCRtpSender는 RTCPeerConnection의 `addTrack()` 메서드를 통해 생성됩니다. 이 메서드는 특정 미디어 트랙을 연결에 추가하고, 해당 트랙의 송신자를 반환합니다.

#### 기본 문법
```javascript
const sender = peerConnection.addTrack(track, stream);
```
- `track`: 전송할 MediaStreamTrack 객체.
- `stream`: 해당 트랙이 포함된 MediaStream 객체.

### 속성 및 메서드
- `rtpParameters`: 현재 RTP 매개변수를 반환합니다.
- `replaceTrack(track)`: 송신할 트랙을 교체합니다.
- `setParameters(parameters)`: 송신 매개변수를 설정합니다.
  
## 예제
### 기본 사용 예제
```javascript
// RTCPeerConnection 생성
const peerConnection = new RTCPeerConnection();

// MediaStream 생성 및 트랙 추가
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
  .then(stream => {
    stream.getTracks().forEach(track => {
      peerConnection.addTrack(track, stream);
    });
  });
```

### 트랙 교체 예제
```javascript
// 기존 트랙을 새로운 트랙으로 교체
const newTrack = await getNewVideoTrack(); // 새로운 비디오 트랙을 가져오는 함수
const sender = peerConnection.getSenders().find(s => s.track.kind === 'video');
sender.replaceTrack(newTrack);
```

## 설명
RTCRtpSender를 사용할 때 주의해야 할 점은 다음과 같습니다:

1. **트랙 상태 관리**: 송신 트랙이 비활성화되거나 제거되면 RTCRtpSender는 더 이상 데이터를 전송하지 않습니다. 트랙 상태를 주의 깊게 관리해야 합니다.
  
2. **전송 품질 설정**: 전송 품질을 조정할 때는 `setParameters` 메서드를 사용하여 비트레이트, 프레임 레이트 등의 매개변수를 설정할 수 있습니다. 그러나 지원되는 매개변수는 브라우저와 네트워크 환경에 따라 다를 수 있습니다.

3. **호환성**: 모든 브라우저가 WebRTC API를 완벽하게 지원하지 않으므로, 사용할 기능이 브라우저에서 지원되는지 확인해야 합니다.

## 한 줄 요약
RTCRtpSender는 WebRTC에서 미디어 스트림을 전송하는 데 필수적인 객체로, 다양한 기능을 통해 전송 품질을 조절할 수 있습니다.