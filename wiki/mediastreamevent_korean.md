<!--
Meta Description: # MediaStreamEvent: JavaScript에서 미디어 스트림 이벤트 이해하기 ## 개요 MediaStreamEvent는 JavaScript에서 미디어 스트림의 변화를 감지하고 처리하기 위한 이벤트를 정의하는 객체입니다. 주로 WebRTC 및 미디어 스트리밍...
Meta Keywords: 미디어, 스트림이, mediastreamevent, 이벤트, mediastream
-->

# MediaStreamEvent: JavaScript에서 미디어 스트림 이벤트 이해하기

## 개요
MediaStreamEvent는 JavaScript에서 미디어 스트림의 변화를 감지하고 처리하기 위한 이벤트를 정의하는 객체입니다. 주로 WebRTC 및 미디어 스트리밍 API에서 사용되며, 오디오 및 비디오 데이터를 다룰 때 유용합니다.

## 문서
MediaStreamEvent는 `MediaStream` 객체와 관련된 특정 이벤트를 나타냅니다. 이 이벤트는 주로 미디어 스트림이 추가되거나 제거될 때 발생하며, 개발자는 이를 통해 스트림의 상태 변화를 실시간으로 처리할 수 있습니다.

### 목적
MediaStreamEvent의 주요 목적은 미디어 스트림의 변화를 청취하고 이에 대한 반응을 정의하는 것입니다. 예를 들어, 사용자가 카메라 또는 마이크를 추가하거나 제거할 때 이 이벤트를 통해 애플리케이션이 적절히 대응할 수 있습니다.

### 사용법
MediaStreamEvent는 `MediaStream` 객체와 함께 사용되며, 이벤트 리스너를 추가하여 특정 이벤트에 대한 반응을 정의합니다.

```javascript
const mediaStream = new MediaStream();

// 미디어 스트림 이벤트 리스너 추가
mediaStream.addEventListener('active', (event) => {
    console.log('미디어 스트림이 활성화되었습니다.');
});

mediaStream.addEventListener('inactive', (event) => {
    console.log('미디어 스트림이 비활성화되었습니다.');
});
```

## 예제
기본적인 MediaStreamEvent 사용 예제는 다음과 같습니다.

### 예제 1: 스트림이 활성화될 때
```javascript
navigator.mediaDevices.getUserMedia({ video: true })
    .then(stream => {
        const mediaStreamEvent = new MediaStreamEvent('active', { stream });
        console.log('스트림이 활성화되었습니다:', mediaStreamEvent);
    })
    .catch(error => {
        console.error('스트림 활성화 실패:', error);
    });
```

### 예제 2: 스트림이 비활성화될 때
```javascript
navigator.mediaDevices.getUserMedia({ audio: true })
    .then(stream => {
        stream.getAudioTracks()[0].stop();
        const mediaStreamEvent = new MediaStreamEvent('inactive', { stream });
        console.log('스트림이 비활성화되었습니다:', mediaStreamEvent);
    })
    .catch(error => {
        console.error('스트림 비활성화 실패:', error);
    });
```

## 설명
MediaStreamEvent를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **이벤트 이름**: 이벤트 이름이 'active' 또는 'inactive'과 같은 정해진 이름이어야 합니다. 잘못된 이름을 사용할 경우 이벤트가 발생하지 않습니다.
- **비동기 처리**: `getUserMedia`와 같은 비동기 메소드 사용 시, 스트림이 준비되기 전에 이벤트를 청취하면 오류가 날 수 있습니다. 따라서 반드시 스트림이 준비된 후에 이벤트 리스너를 추가해야 합니다.

## 한 줄 요약
MediaStreamEvent는 JavaScript에서 미디어 스트림의 활성화 및 비활성화를 감지하여 처리하는 데 사용되는 이벤트 객체입니다.