<!--
Meta Description: # JavaScript onseeked 이벤트: 비디오 및 오디오 플레이어의 중재 ## 개요 `onseeked` 이벤트는 HTMLMediaElement에서 사용되며, 사용자가 비디오 또는 오디오 요소의 재생 위치를 변경한 후 발생합니다. 이 이벤트는 사용자 인터페이스에...
Meta Keywords: video, onseeked, 있습니다, 이벤트는, 이벤트
-->

# JavaScript onseeked 이벤트: 비디오 및 오디오 플레이어의 중재

## 개요
`onseeked` 이벤트는 HTMLMediaElement에서 사용되며, 사용자가 비디오 또는 오디오 요소의 재생 위치를 변경한 후 발생합니다. 이 이벤트는 사용자 인터페이스에서 미디어 파일의 재생 상태를 업데이트하는 데 유용합니다.

## 문서화
### 목적
`onseeked` 이벤트는 비디오 또는 오디오의 재생 위치가 변경된 후에 발생합니다. 이는 사용자가 시크 바를 조작하거나 특정 시간으로 점프했을 때 발생합니다. 이벤트가 발생하면 미디어 파일의 새로운 재생 상태를 반영할 수 있습니다.

### 사용법
`onseeked` 이벤트는 HTMLMediaElement(예: `<video>` 또는 `<audio>`)에서 사용할 수 있습니다. 이벤트 리스너를 추가하여 사용자는 미디어 요소의 상태를 제어할 수 있습니다.

```javascript
const video = document.querySelector('video');

video.onseeked = function() {
    console.log('Seeked to new position: ' + video.currentTime);
};
```

### 세부사항
- **이벤트 타입**: `Event`
- **이벤트 발생**: 사용자가 재생 위치를 변경한 후.
- **지원 브라우저**: 모든 주요 브라우저에서 지원.
- **속성**: 
  - `currentTime`: 현재 재생 중인 미디어의 시간(초 단위).

## 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onseeked 이벤트 예제</title>
</head>
<body>
    <video id="myVideo" controls>
        <source src="video.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>

    <script>
        const video = document.getElementById('myVideo');

        video.onseeked = function() {
            console.log('현재 재생 위치: ' + video.currentTime + '초');
        };
    </script>
</body>
</html>
```

## 설명
- **일반적인 문제점**: 
  - `onseeked` 이벤트가 예상보다 자주 발생할 수 있습니다. 예를 들어 사용자가 빠르게 여러 번 클릭하면 여러 번 호출될 수 있습니다.
  - 이벤트가 발생하기 전에 `currentTime` 속성이 업데이트된 후에 코드가 실행되므로, 이벤트를 처리하는 로직에서 주의해야 합니다.

- **주의사항**:
  - 이 이벤트는 `onseekstart` 이벤트와 함께 사용되어 seek 동작의 시작과 끝을 모두 처리할 수 있습니다.
  - 비디오가 로드되지 않았거나 재생이 불가능한 경우, `currentTime`을 설정하려고 하면 오류가 발생할 수 있습니다.

## 한 줄 요약
`onseeked` 이벤트는 사용자가 비디오 또는 오디오의 재생 위치를 변경한 후 발생하며, 현재 재생 상태를 반영하는 데 유용합니다.