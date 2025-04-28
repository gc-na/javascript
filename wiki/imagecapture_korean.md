<!--
Meta Description: # ImageCapture: JavaScript로 이미지 캡처하기 ## 개요 `ImageCapture`는 JavaScript에서 웹캠이나 비디오 스트림으로부터 이미지를 캡처하는 데 사용되는 API입니다. 이 API는 실시간 비디오 스트림에서 고해상도 이미지를 쉽게 추출...
Meta Keywords: imagecapture, const, error, 비디오, img
-->

# ImageCapture: JavaScript로 이미지 캡처하기

## 개요
`ImageCapture`는 JavaScript에서 웹캠이나 비디오 스트림으로부터 이미지를 캡처하는 데 사용되는 API입니다. 이 API는 실시간 비디오 스트림에서 고해상도 이미지를 쉽게 추출할 수 있게 해줍니다.

## 문서화
`ImageCapture`는 MediaStreamTrack에서 사용되며, 비디오 스트림에서 개별 이미지를 캡처할 수 있는 기능을 제공합니다. 주로 웹캠과 같은 입력 장치에서 이미지 프레임을 가져오는 데 유용합니다. 

### 목적
- 비디오 스트림에서 이미지를 캡처하고 처리하기 위한 API 제공
- 실시간 비디오 데이터에서 특정 이미지를 추출 가능

### 사용법
1. **MediaStreamTrack 가져오기**: 먼저, 웹캠 또는 비디오 스트림을 가져와야 합니다.
2. **ImageCapture 인스턴스 생성**: 가져온 MediaStreamTrack을 사용하여 `ImageCapture` 인스턴스를 생성합니다.
3. **이미지 캡처**: `grabFrame()` 또는 `takePhoto()` 메서드를 사용하여 이미지를 캡처합니다.

### 기본 구조
```javascript
navigator.mediaDevices.getUserMedia({ video: true })
  .then(stream => {
    const videoTrack = stream.getVideoTracks()[0];
    const imageCapture = new ImageCapture(videoTrack);

    return imageCapture.takePhoto();
  })
  .then(blob => {
    const img = document.createElement('img');
    img.src = URL.createObjectURL(blob);
    document.body.appendChild(img);
  })
  .catch(error => console.error('Error:', error));
```

## 예제
### 예제 1: 단순 이미지 캡처
```javascript
async function captureImage() {
  const stream = await navigator.mediaDevices.getUserMedia({ video: true });
  const track = stream.getVideoTracks()[0];
  const imageCapture = new ImageCapture(track);

  try {
    const blob = await imageCapture.takePhoto();
    const img = document.createElement('img');
    img.src = URL.createObjectURL(blob);
    document.body.appendChild(img);
  } catch (error) {
    console.error('Error capturing photo:', error);
  }
}

captureImage();
```

### 예제 2: 이미지 프레임 가져오기
```javascript
async function grabFrame() {
  const stream = await navigator.mediaDevices.getUserMedia({ video: true });
  const track = stream.getVideoTracks()[0];
  const imageCapture = new ImageCapture(track);

  try {
    const imageBitmap = await imageCapture.grabFrame();
    const canvas = document.createElement('canvas');
    canvas.width = imageBitmap.width;
    canvas.height = imageBitmap.height;

    const ctx = canvas.getContext('2d');
    ctx.drawImage(imageBitmap, 0, 0);
    document.body.appendChild(canvas);
  } catch (error) {
    console.error('Error grabbing frame:', error);
  }
}

grabFrame();
```

## 설명
- **브라우저 호환성**: `ImageCapture`는 모든 브라우저에서 지원되지 않으므로, 사용 전에 호환성을 확인해야 합니다.
- **비디오 트랙**: `ImageCapture`는 반드시 비디오 트랙에서만 사용해야 하며, 오디오 트랙에서는 사용할 수 없습니다.
- **권한 요청**: 사용자가 카메라에 접근할 수 있도록 권한을 요청해야 하며, 사용자가 이를 허용하지 않으면 API를 사용할 수 없습니다.

## 한 줄 요약
`ImageCapture`는 JavaScript에서 비디오 스트림으로부터 고해상도 이미지를 쉽게 캡처할 수 있게 해주는 API입니다.