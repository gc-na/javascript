<!--
Meta Description: # JavaScript의 onloadedmetadata 이벤트: 사용법과 예제 ## 개요 `onloadedmetadata`는 HTMLMediaElement의 메타데이터가 로드되었을 때 발생하는 이벤트로, 비디오나 오디오의 정보(예: 길이, 크기, 해상도 등)를 활용할 ...
Meta Keywords: onloadedmetadata, video, audio, 이벤트는, 비디오
-->

# JavaScript의 onloadedmetadata 이벤트: 사용법과 예제

## 개요
`onloadedmetadata`는 HTMLMediaElement의 메타데이터가 로드되었을 때 발생하는 이벤트로, 비디오나 오디오의 정보(예: 길이, 크기, 해상도 등)를 활용할 수 있게 해줍니다.

## 문서화
`onloadedmetadata` 이벤트는 미디어 파일이 로드되었을 때 발생하며, 주로 `<video>` 및 `<audio>` 요소에서 사용됩니다. 이 이벤트는 메타데이터가 준비된 후에 발생하므로, 사용자는 비디오/오디오의 길이나 다른 중요한 속성에 접근할 수 있습니다.

### 목적
이 이벤트는 미디어 파일에 대한 정보를 얻기 위해 필요합니다. 예를 들어, 사용자에게 재생 시간이나 총 길이를 표시할 때 유용합니다.

### 사용법
`onloadedmetadata` 이벤트는 다음과 같은 방식으로 사용할 수 있습니다:

```javascript
const videoElement = document.querySelector('video');

videoElement.onloadedmetadata = function() {
    console.log('비디오의 길이:', videoElement.duration);
};
```

또는 `addEventListener` 메소드를 사용할 수도 있습니다:

```javascript
videoElement.addEventListener('loadedmetadata', function() {
    console.log('비디오의 길이:', videoElement.duration);
});
```

## 예제
1. **비디오 메타데이터 로드 시 길이 출력하기**

```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    브라우저가 비디오 태그를 지원하지 않습니다.
</video>

<script>
    const video = document.getElementById('myVideo');
    
    video.onloadedmetadata = function() {
        console.log('비디오 길이:', video.duration);
    };
</script>
```

2. **오디오 메타데이터 로드 시 정보 출력하기**

```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mp3">
    브라우저가 오디오 태그를 지원하지 않습니다.
</audio>

<script>
    const audio = document.getElementById('myAudio');
    
    audio.addEventListener('loadedmetadata', function() {
        console.log('오디오 길이:', audio.duration);
    });
</script>
```

## 설명
- **일반적인 함정**: `onloadedmetadata` 이벤트는 미디어 파일의 메타데이터가 로드되기 전에 설정되면 작동하지 않을 수 있습니다. 따라서, 반드시 미디어 파일이 로드된 후에 이 이벤트 핸들러를 설정해야 합니다.
  
- **브라우저 호환성**: 대부분의 현대 브라우저에서 지원되지만, 구식 브라우저에서는 동작하지 않을 수 있으므로, 필요한 경우 폴리필을 고려해야 합니다.

- **이벤트 순서**: 이 이벤트는 `loadeddata` 이벤트보다 먼저 발생합니다. 따라서 메타데이터를 기반으로 한 처리를 원할 경우 이 이벤트를 사용해야 합니다.

## 한 문장 요약
`onloadedmetadata` 이벤트는 HTMLMediaElement의 메타데이터가 로드되었을 때 발생하여, 비디오 및 오디오의 중요한 정보를 활용할 수 있게 해주는 이벤트입니다.