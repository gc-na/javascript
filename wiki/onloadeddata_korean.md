<!--
Meta Description: # JavaScript의 onloadeddata 이벤트: 미디어 데이터 로드 완료 시 발생하는 이벤트 ## 개요 `onloadeddata` 이벤트는 HTMLMediaElement(예: `<audio>`, `<video>`)에서 미디어 데이터가 로드되어 사용 가능해질 때...
Meta Keywords: 미디어, video, 이벤트, audio, 있습니다
-->

# JavaScript의 onloadeddata 이벤트: 미디어 데이터 로드 완료 시 발생하는 이벤트

## 개요
`onloadeddata` 이벤트는 HTMLMediaElement(예: `<audio>`, `<video>`)에서 미디어 데이터가 로드되어 사용 가능해질 때 발생합니다. 이 이벤트는 미디어 파일이 준비되었음을 알려주며, 이를 통해 사용자에게 재생 준비 상태를 알리거나 추가적인 작업을 수행할 수 있습니다.

## 문서화
### 목적
`onloadeddata` 이벤트는 미디어 요소가 필요한 데이터의 일부 또는 전부를 로드했을 때 발생합니다. 이는 사용자가 미디어 파일을 재생하기 전에 필요한 데이터를 모두 로드했음을 확인할 수 있도록 도와줍니다.

### 사용법
이 이벤트는 HTMLMediaElement의 이벤트 핸들러로 설정하여 사용합니다. JavaScript 코드 내에서 `addEventListener` 메서드를 사용하여 이벤트 리스너를 추가할 수 있습니다.

```javascript
const videoElement = document.querySelector('video');

videoElement.addEventListener('loadeddata', function() {
    console.log('비디오 데이터가 로드되었습니다.');
});
```

### 세부사항
- **이벤트 발생 시기**: 미디어 데이터가 로드될 때마다 발생하며, 이는 사용자가 데이터를 요청한 후에 이루어집니다.
- **이벤트 리스너**: `onloadeddata` 이벤트는 HTMLMediaElement의 모든 인스턴스에서 사용할 수 있으며, 단일 이벤트 리스너를 추가하여 여러 미디어 요소에서 동시에 사용할 수 있습니다.
- **호환성**: 대부분의 최신 브라우저에서 지원되며, 이전 버전의 브라우저에서는 지원이 제한될 수 있습니다.

## 예제
### 기본 사용 예제
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');

    video.addEventListener('loadeddata', () => {
        console.log('비디오 데이터가 성공적으로 로드되었습니다.');
    });
</script>
```

### 추가적인 예제
```javascript
const audio = new Audio('audio.mp3');

audio.addEventListener('loadeddata', () => {
    console.log('오디오 데이터가 준비되었습니다. 재생 시작!');
    audio.play();
});

audio.load();
```

## 설명
`onloadeddata` 이벤트를 사용할 때 몇 가지 주의사항이 있습니다:

- **비디오/오디오 형식**: 모든 형식의 비디오 및 오디오 파일이 동일하게 로드되지 않으므로, 형식에 따라 성능이 달라질 수 있습니다.
- **네트워크 지연**: 네트워크 속도에 따라 로딩 시간이 달라질 수 있으며, 이로 인해 사용자가 예상보다 느리게 콘텐츠를 재생할 수 있습니다.
- **브라우저 호환성**: 일부 오래된 브라우저에서는 이 이벤트를 지원하지 않을 수 있으므로, 이를 고려하여 폴리필을 적용하는 것도 좋은 방법입니다.

## 한줄 요약
`onloadeddata` 이벤트는 HTMLMediaElement에서 미디어 데이터가 로드 완료될 때 발생하여, 미디어 재생 준비 상태를 인지할 수 있게 해줍니다.