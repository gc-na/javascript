<!--
Meta Description: # MediaRecorder: JavaScript를 이용한 실시간 미디어 녹화 ## 개요 MediaRecorder는 JavaScript API로, 사용자가 웹 브라우저에서 실시간으로 오디오와 비디오를 녹화할 수 있도록 해줍니다. 이 기능은 주로 웹 애플리케이션에서 비디...
Meta Keywords: mediarecorder, const, blob, error, 있습니다
-->

# MediaRecorder: JavaScript를 이용한 실시간 미디어 녹화

## 개요
MediaRecorder는 JavaScript API로, 사용자가 웹 브라우저에서 실시간으로 오디오와 비디오를 녹화할 수 있도록 해줍니다. 이 기능은 주로 웹 애플리케이션에서 비디오 스트리밍, 화상 회의, 게임 방송 등 다양한 상황에서 활용됩니다.

## 문서화

### 목적
MediaRecorder API는 웹 애플리케이션에서 미디어 데이터를 녹화하고, 이를 Blob 형식으로 저장하여 나중에 다운로드하거나 서버에 전송할 수 있게 해줍니다.

### 사용법
MediaRecorder를 사용하기 위해서는 먼저 MediaStream을 생성해야 합니다. 이는 getUserMedia() 메서드를 통해 카메라와 마이크에 접근하여 얻을 수 있습니다.

#### 기본 문법
```javascript
const mediaRecorder = new MediaRecorder(mediaStream, options);
```

- **mediaStream**: 녹화할 미디어 스트림 (VideoStream 또는 AudioStream)
- **options**: 선택적 설정으로, MIME 타입 등을 정의할 수 있습니다.

### 주요 메서드
- `start()`: 녹화를 시작합니다.
- `stop()`: 녹화를 중지합니다.
- `pause()`: 녹화를 일시 정지합니다.
- `resume()`: 일시 정지된 녹화를 재개합니다.

### 이벤트
- `dataavailable`: 녹화된 데이터가 준비되었을 때 발생합니다.
- `start`: 녹화가 시작되었을 때 발생합니다.
- `stop`: 녹화가 중지되었을 때 발생합니다.
- `error`: 녹화 중 오류가 발생했을 때 발생합니다.

## 예제

### 기본 사용 예제
```javascript
// 사용자의 카메라와 마이크에 접근
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
  .then((stream) => {
    const mediaRecorder = new MediaRecorder(stream);
    const recordedChunks = [];

    mediaRecorder.ondataavailable = (event) => {
      if (event.data.size > 0) {
        recordedChunks.push(event.data);
      }
    };

    mediaRecorder.onstop = () => {
      const blob = new Blob(recordedChunks, { type: 'video/webm' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'recording.webm';
      document.body.appendChild(a);
      a.click();
    };

    mediaRecorder.start();

    // 5초 후 녹화 중지
    setTimeout(() => {
      mediaRecorder.stop();
    }, 5000);
  })
  .catch((error) => {
    console.error('Error accessing media devices.', error);
  });
```

## 설명
MediaRecorder API를 사용할 때 주의할 점은 다음과 같습니다:
- 브라우저 호환성: 모든 브라우저가 MediaRecorder API를 지원하지 않으므로, 사용하기 전에 호환성을 확인해야 합니다.
- 보안: HTTPS 환경에서만 getUserMedia()를 사용할 수 있습니다.
- MIME 타입: 사용하려는 형식이 브라우저에서 지원되는지 확인해야 합니다.
- 이벤트 핸들링: 데이터가 준비되기 전에 stop() 메서드를 호출하면 데이터가 누락될 수 있습니다.

## 한 줄 요약
MediaRecorder는 JavaScript를 통해 실시간으로 오디오와 비디오를 녹화하고, 이를 Blob 형식으로 저장할 수 있는 강력한 API입니다.