<!--
Meta Description: # JavaScript에서 onplay 이벤트 처리하기 ## 개요 `onplay`는 HTMLMediaElement의 이벤트 중 하나로, 미디어(비디오 또는 오디오)가 재생을 시작할 때 발생합니다. 이 이벤트는 JavaScript를 사용하여 미디어를 제어할 때 유용하게 ...
Meta Keywords: onplay, 비디오가, video, videoelement, 이벤트
-->

# JavaScript에서 onplay 이벤트 처리하기

## 개요
`onplay`는 HTMLMediaElement의 이벤트 중 하나로, 미디어(비디오 또는 오디오)가 재생을 시작할 때 발생합니다. 이 이벤트는 JavaScript를 사용하여 미디어를 제어할 때 유용하게 활용될 수 있습니다.

## 문서화

### 목적
`onplay` 이벤트는 사용자가 미디어 콘텐츠를 재생할 때 발생하는 신호를 제공합니다. 이 이벤트를 활용하면 재생 시작 시 특정 작업을 수행하거나 UI를 업데이트할 수 있습니다.

### 사용법
`onplay` 이벤트는 HTMLMediaElement(예: `<video>` 또는 `<audio>` 태그)의 인스턴스에 직접 할당하거나 `addEventListener` 메서드를 사용하여 등록할 수 있습니다.

```javascript
const videoElement = document.getElementById('myVideo');

// onplay 속성 사용
videoElement.onplay = function() {
    console.log('비디오가 재생됩니다.');
};

// addEventListener 사용
videoElement.addEventListener('play', function() {
    console.log('비디오가 재생됩니다.');
});
```

## 예제

### 기본 사용 예제
아래 예제는 비디오가 재생될 때 콘솔에 메시지를 출력합니다.

```html
<video id="myVideo" width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    브라우저가 비디오 태그를 지원하지 않습니다.
</video>

<script>
    const videoElement = document.getElementById('myVideo');
    
    videoElement.onplay = function() {
        console.log('비디오가 재생됩니다.');
    };
</script>
```

### UI 업데이트 예제
비디오가 재생될 때 UI 요소를 업데이트하는 예제입니다.

```html
<div id="status">비디오가 재생되지 않습니다.</div>
<video id="myVideo" width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    브라우저가 비디오 태그를 지원하지 않습니다.
</video>

<script>
    const videoElement = document.getElementById('myVideo');
    const statusDiv = document.getElementById('status');
    
    videoElement.onplay = function() {
        statusDiv.textContent = '비디오가 재생 중입니다.';
    };
</script>
```

## 설명
- **이벤트 발생**: `onplay` 이벤트는 비디오가 재생될 때 단 한 번 발생하며, 사용자가 일시 정지 후 다시 재생하면 다시 발생합니다.
- **브라우저 지원**: 대부분의 현대 브라우저에서 지원되지만, 특정 환경에서는 다르게 동작할 수 있습니다.
- **추가 이벤트**: `onplay` 이벤트와 함께 `pause`, `ended`와 같은 다른 이벤트를 조합하여 미디어 플레이어의 상태를 보다 세밀하게 제어할 수 있습니다.

### 일반적인 실수
- `onplay`를 단순히 HTML 요소에 직접 설정하는 것보다 `addEventListener`를 사용하는 것이 더 유연합니다.
- 가끔 이벤트 핸들러에서 비동기 작업을 수행하는 경우, 예상치 못한 동작이 발생할 수 있으므로 주의가 필요합니다.

## 한 줄 요약
`onplay` 이벤트는 비디오 또는 오디오가 재생될 때 발생하며, JavaScript를 통해 사용자 인터페이스를 업데이트하거나 특정 작업을 수행하는 데 유용합니다.