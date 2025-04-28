<!--
Meta Description: # MediaStream: 자바스크립트에서의 사용법과 예제 ## 개요 MediaStream은 웹 브라우저에서 비디오 및 오디오 미디어 데이터를 처리하고 전송하기 위한 API입니다. 이 API는 특히 WebRTC(웹 실시간 통신) 및 미디어 처리 애플리케이션에서 중요한 ...
Meta Keywords: mediastream, 미디어, video, error, stream
-->

# MediaStream: 자바스크립트에서의 사용법과 예제

## 개요
MediaStream은 웹 브라우저에서 비디오 및 오디오 미디어 데이터를 처리하고 전송하기 위한 API입니다. 이 API는 특히 WebRTC(웹 실시간 통신) 및 미디어 처리 애플리케이션에서 중요한 역할을 합니다.

## 문서화
MediaStream은 사용자가 특정 미디어 소스(예: 카메라, 마이크)로부터 데이터를 캡처하고 이를 웹 애플리케이션에서 실시간으로 사용할 수 있도록 해주는 객체입니다. 이 객체는 미디어 데이터를 스트리밍하고 처리하는 데 필수적인 기능을 제공합니다.

### 목적
- 웹 애플리케이션에서 실시간 미디어 스트리밍을 지원
- 카메라와 마이크와 같은 다양한 미디어 장치로부터 데이터 캡처
- WebRTC와 같은 기술과 통합하여 실시간 통신 구현

### 사용법
MediaStream 객체는 `getUserMedia()` 메서드를 통해 생성됩니다. 이 메서드는 사용자에게 카메라 및 마이크 접근을 요청하고, 허가를 받으면 MediaStream을 반환합니다.

```javascript
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
  .then(stream => {
    // 스트림을 사용하여 비디오 요소에 연결
    const videoElement = document.querySelector('video');
    videoElement.srcObject = stream;
    videoElement.play();
  })
  .catch(error => {
    console.error('MediaStream 생성 중 오류 발생:', error);
  });
```

## 예제
### 기본 사용 예
사용자가 카메라와 마이크에 접근하여 비디오와 오디오를 스트리밍하는 간단한 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MediaStream 예제</title>
</head>
<body>
    <video autoplay></video>
    <script>
        navigator.mediaDevices.getUserMedia({ video: true, audio: true })
            .then(stream => {
                const videoElement = document.querySelector('video');
                videoElement.srcObject = stream;
            })
            .catch(error => {
                console.error('MediaStream 생성 중 오류 발생:', error);
            });
    </script>
</body>
</html>
```

## 설명
### 일반적인 문제점 및 주의 사항
- **브라우저 호환성**: MediaStream API는 모든 브라우저에서 동일하게 지원되지 않을 수 있습니다. Chrome, Firefox, Edge에서 주로 사용되지만 Safari에서는 제한적일 수 있습니다.
- **HTTPS 요구사항**: 보안상의 이유로, getUserMedia() 메서드는 HTTPS 환경에서만 작동합니다. 로컬 개발에서는 `localhost`도 허용됩니다.
- **사용자 허가**: 사용자가 카메라 또는 마이크 접근을 허가하지 않으면 오류가 발생합니다. 이를 처리하기 위한 적절한 에러 핸들링이 필요합니다.
- **스트림 해제**: 사용이 끝난 후에는 스트림을 해제해야 합니다. 이를 위해 `MediaStream.getTracks()` 메서드를 사용하여 각 트랙을 종료할 수 있습니다.

```javascript
stream.getTracks().forEach(track => track.stop());
```

## 한 줄 요약
MediaStream은 자바스크립트를 통해 실시간으로 비디오 및 오디오 데이터를 처리하고 스트리밍할 수 있게 해주는 강력한 API입니다.