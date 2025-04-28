<!--
Meta Description: # JavaScript의 ondurationchange 이벤트에 대한 완벽 가이드 ## 개요 `ondurationchange` 이벤트는 HTMLMediaElement의 duration 속성이 변경될 때 발생하며, 주로 비디오 및 오디오 요소에서 사용됩니다. 이 이벤트를...
Meta Keywords: audio, video, ondurationchange, 미디어의, 이벤트는
-->

# JavaScript의 ondurationchange 이벤트에 대한 완벽 가이드

## 개요
`ondurationchange` 이벤트는 HTMLMediaElement의 duration 속성이 변경될 때 발생하며, 주로 비디오 및 오디오 요소에서 사용됩니다. 이 이벤트를 통해 미디어의 길이가 변경되었을 때의 처리를 손쉽게 구현할 수 있습니다.

## 문서화
### 목적
`ondurationchange` 이벤트는 미디어의 지속 시간이 변경될 때 발생하여, 개발자가 미디어의 길이에 대한 변화를 감지하고 적절한 작업을 수행할 수 있도록 돕습니다. 예를 들어, 사용자가 스트리밍 중인 비디오의 길이가 변경되면, 이를 감지하여 사용자 인터페이스를 업데이트할 수 있습니다.

### 사용법
`ondurationchange` 이벤트는 HTMLMediaElement 객체에 대해 발생하며, 주로 `audio` 또는 `video` 요소에서 사용됩니다. 이벤트 리스너를 추가하여 특정 작업을 수행할 수 있습니다.

```javascript
const videoElement = document.querySelector('video');

videoElement.ondurationchange = function() {
    console.log('비디오의 지속 시간이 변경되었습니다: ' + videoElement.duration);
};
```

### 세부 정보
- **타입**: 이벤트
- **이벤트 대상**: HTMLMediaElement (예: `<audio>`, `<video>`)
- **이벤트 발생 시점**: 미디어의 duration 속성이 변경될 때마다 발생합니다.

## 예제
### 기본 사용 예
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    브라우저가 video 태그를 지원하지 않습니다.
</video>

<script>
    const video = document.getElementById('myVideo');

    video.ondurationchange = function() {
        console.log('현재 비디오의 길이: ' + video.duration + '초');
    };
</script>
```

### 스트리밍 예제
```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mpeg">
    브라우저가 audio 태그를 지원하지 않습니다.
</audio>

<script>
    const audio = document.getElementById('myAudio');

    audio.ondurationchange = function() {
        alert('오디오의 길이가 변경되었습니다: ' + audio.duration + '초');
    };
</script>
```

## 설명
- **일반적인 실수**: `ondurationchange` 이벤트는 모든 경우에 발생하지 않을 수 있습니다. 예를 들어, 일부 스트리밍 서비스에서는 미디어의 길이가 명확하게 알려지지 않기 때문에 이 이벤트가 발생하지 않을 수 있습니다.
- **브라우저 호환성**: 대부분의 최신 브라우저에서 지원되지만, 구형 브라우저에서는 지원하지 않을 수 있으므로 확인이 필요합니다.
- **성능 고려사항**: 이벤트가 자주 발생할 수 있으므로, 이벤트 핸들러 내에서의 작업은 최적화하는 것이 좋습니다.

## 한 줄 요약
`ondurationchange` 이벤트는 미디어 요소의 지속 시간이 변경될 때 발생하며, 개발자가 이를 통해 미디어의 길이 변화를 감지하고 필요한 작업을 수행할 수 있도록 돕습니다.