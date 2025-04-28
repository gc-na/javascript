<!--
Meta Description: # JavaScript의 onended 이벤트: 사용법과 예제 ## 개요 `onended`는 HTMLMediaElement 인터페이스의 이벤트로, 미디어 파일(오디오 또는 비디오)이 끝까지 재생되었을 때 발생합니다. 이 이벤트를 활용하면 미디어 재생 완료 시 특정 작업...
Meta Keywords: onended, video, 있습니다, 미디어, audioelement
-->

# JavaScript의 onended 이벤트: 사용법과 예제

## 개요
`onended`는 HTMLMediaElement 인터페이스의 이벤트로, 미디어 파일(오디오 또는 비디오)이 끝까지 재생되었을 때 발생합니다. 이 이벤트를 활용하면 미디어 재생 완료 시 특정 작업을 수행할 수 있습니다.

## 문서화
`onended` 이벤트는 HTMLMediaElement에 포함되어 있으며, 주로 `<audio>` 및 `<video>` 요소와 함께 사용됩니다. 이 이벤트는 미디어가 끝나면 자동으로 트리거 되어, 사용자가 원하는 추가 작업을 쉽게 실행할 수 있게 해줍니다.

### 사용법
이벤트 리스너를 통해 `onended` 이벤트에 대한 반응을 정의할 수 있습니다. 다음은 기본적인 사용법입니다:

```javascript
const audioElement = document.getElementById('myAudio');

audioElement.onended = function() {
    console.log('오디오 재생이 완료되었습니다.');
};
```

또는 `addEventListener` 메서드를 사용하여 이벤트 리스너를 등록할 수도 있습니다:

```javascript
audioElement.addEventListener('ended', function() {
    console.log('오디오 재생이 완료되었습니다.');
});
```

## 예제
### 기본 예제
오디오 파일이 끝났을 때 알림을 표시하는 간단한 예제입니다.

```html
<audio id="myAudio" controls>
    <source src="audiofile.mp3" type="audio/mpeg">
    브라우저가 오디오를 지원하지 않습니다.
</audio>

<script>
const audioElement = document.getElementById('myAudio');

audioElement.onended = function() {
    alert('재생이 끝났습니다!');
};
</script>
```

### 비디오 예제
비디오 파일이 끝났을 때 다른 동영상을 자동으로 재생하는 예제입니다.

```html
<video id="myVideo" width="320" height="240" controls>
    <source src="video1.mp4" type="video/mp4">
    브라우저가 비디오를 지원하지 않습니다.
</video>

<video id="myVideo2" width="320" height="240" controls>
    <source src="video2.mp4" type="video/mp4">
</video>

<script>
const videoElement = document.getElementById('myVideo');
const nextVideo = document.getElementById('myVideo2');

videoElement.onended = function() {
    nextVideo.play();
};
</script>
```

## 설명
`onended` 이벤트는 미디어 스트리밍이나 플레이리스트 기능을 구현할 때 유용하게 사용됩니다. 하지만 몇 가지 주의할 점이 있습니다:

1. **자동 재생**: 일부 브라우저에서는 사용자의 상호작용 없이 자동 재생이 제한될 수 있습니다. 따라서 `onended` 이벤트가 예상대로 작동하지 않을 수도 있습니다.
2. **미디어 형식 지원**: 모든 브라우저가 모든 미디어 형식을 지원하지 않으므로, 사용자에게 적절한 형식을 제공해야 합니다.
3. **비동기 처리**: `onended` 이벤트가 발생한 후에 수행할 작업은 비동기적으로 처리할 수 있어야 합니다. 예를 들어, AJAX 요청을 통해 서버와 통신하는 경우에는 적절한 오류 처리가 필요합니다.

## 한 줄 요약
`onended` 이벤트는 HTMLMediaElement에서 미디어가 끝났을 때 발생하며, 재생 완료 후의 작업을 정의하는 데 유용합니다.