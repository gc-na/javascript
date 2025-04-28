<!--
Meta Description: # MediaStreamTrackVideoStats: JavaScript에서의 비디오 트랙 통계 ## 개요 `MediaStreamTrackVideoStats`는 WebRTC의 일부로, 비디오 스트림의 다양한 통계를 제공하는 객체입니다. 이 객체는 개발자가 비디오 트랙의...
Meta Keywords: 비디오, report, mediastreamtrackvideostats, console, log
-->

# MediaStreamTrackVideoStats: JavaScript에서의 비디오 트랙 통계

## 개요
`MediaStreamTrackVideoStats`는 WebRTC의 일부로, 비디오 스트림의 다양한 통계를 제공하는 객체입니다. 이 객체는 개발자가 비디오 트랙의 성능을 모니터링하고 최적화하는 데 도움을 줍니다.

## 문서화

### 목적
`MediaStreamTrackVideoStats`는 비디오 트랙의 상태 및 성능 정보를 제공하여, 비디오 통화나 스트리밍 서비스의 품질을 개선할 수 있도록 설계되었습니다. 이를 통해 개발자는 전송 품질, 프레임률, 해상도 등의 중요한 메트릭을 추적할 수 있습니다.

### 사용법
`MediaStreamTrackVideoStats` 객체는 `getStats()` 메서드를 통해 얻을 수 있습니다. 이 메서드는 `RTCPeerConnection` 또는 `MediaStream` 객체에 연결된 트랙의 실시간 통계 정보를 반환합니다.

### 세부사항
- **속성**:
  - `trackId`: 비디오 트랙의 고유 식별자.
  - `frameWidth`: 비디오 프레임의 너비.
  - `frameHeight`: 비디오 프레임의 높이.
  - `framesPerSecond`: 초당 전송되는 프레임 수.
  - `totalFrames`: 전송된 총 프레임 수.
  - `timestamp`: 가장 최근에 업데이트된 시간.

## 예제

```javascript
// RTCPeerConnection을 생성합니다.
const peerConnection = new RTCPeerConnection();

// 비디오 트랙을 추가합니다.
const videoTrack = peerConnection.addTrack(videoStream.getVideoTracks()[0]);

// getStats() 메서드를 사용하여 통계 정보를 가져옵니다.
peerConnection.getStats(videoTrack).then(stats => {
    stats.forEach(report => {
        if (report.type === 'video') {
            console.log('Track ID:', report.trackId);
            console.log('Frame Width:', report.frameWidth);
            console.log('Frame Height:', report.frameHeight);
            console.log('Frames Per Second:', report.framesPerSecond);
            console.log('Total Frames:', report.totalFrames);
            console.log('Timestamp:', report.timestamp);
        }
    });
});
```

## 설명
`MediaStreamTrackVideoStats`를 사용할 때 주의해야 할 사항은 다음과 같습니다:
- `getStats()` 메서드는 비동기적으로 작동하므로, 결과를 처리할 때 `Promise`를 사용해야 합니다.
- 통계는 실시간으로 업데이트되므로, 호출 시점에 따라 다른 값을 반환할 수 있습니다.
- 웹 브라우저의 호환성에 따라 지원되는 속성이 다를 수 있으며, 이를 확인해야 합니다.

## 한 줄 요약
`MediaStreamTrackVideoStats`는 JavaScript에서 비디오 스트림의 성능 통계를 제공하여 개발자가 비디오 품질을 효과적으로 모니터링하고 최적화할 수 있도록 돕는 객체입니다.