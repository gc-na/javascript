<!--
Meta Description: # JavaScript의 ontimeupdate 이벤트: 비디오 및 오디오 컨트롤 최적화 ## 개요 `ontimeupdate` 이벤트는 HTMLMediaElement의 이벤트 중 하나로, 비디오 또는 오디오 재생 위치가 변경될 때마다 발생합니다. 이 이벤트는 미디어의 ...
Meta Keywords: ontimeupdate, video, 이벤트, 이벤트는, 비디오
-->

# JavaScript의 ontimeupdate 이벤트: 비디오 및 오디오 컨트롤 최적화

## 개요
`ontimeupdate` 이벤트는 HTMLMediaElement의 이벤트 중 하나로, 비디오 또는 오디오 재생 위치가 변경될 때마다 발생합니다. 이 이벤트는 미디어의 현재 시간 정보에 접근할 수 있는 유용한 방법을 제공합니다. 

## 문서화
### 목적
`ontimeupdate` 이벤트는 비디오 또는 오디오 파일의 재생 중 사용자가 현재 재생 시간을 확인하거나 특정 동작을 수행할 수 있도록 돕습니다. 이 이벤트는 주로 UI 업데이트나 사용자 상호작용을 위해 사용됩니다.

### 사용법
`ontimeupdate` 이벤트는 HTMLMediaElement(예: `<video>` 또는 `<audio>` 태그)의 인스턴스에서 사용할 수 있습니다. 이 이벤트는 JavaScript에서 이벤트 리스너를 통해 처리할 수 있습니다.

#### 기본 구문
```javascript
mediaElement.ontimeupdate = function() {
    // 이벤트가 발생할 때 실행할 코드
};
```

### 상세 내용
- **이벤트 발생 시기**: 비디오나 오디오의 재생 위치가 변경될 때마다 발생합니다. 이는 사용자가 미디어를 재생, 일시 정지, 또는 특정 위치로 이동할 때 모두 포함됩니다.
- **속성**: 이벤트 객체는 `currentTime` 속성을 통해 현재 재생 시간을 초 단위로 제공합니다.
- **브라우저 지원**: 대부분의 현대 브라우저에서 지원되지만, 구형 브라우저에서는 다르게 동작할 수 있습니다.

## 예제
### 기본 사용 예제
다음은 비디오 재생 위치가 변경될 때마다 현재 시간을 콘솔에 출력하는 간단한 예제입니다.

```html
<video id="myVideo" width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');
    
    video.ontimeupdate = function() {
        console.log("현재 시간: " + video.currentTime + "초");
    };
</script>
```

## 설명
`ontimeupdate` 이벤트를 사용할 때 주의할 점은 다음과 같습니다:
- **성능 문제**: 매우 짧은 시간 간격으로 이벤트가 발생하므로, 이 이벤트를 사용할 때는 성능에 영향을 미치지 않도록 주의해야 합니다. 예를 들어, 이벤트 핸들러 내에서 불필요한 DOM 조작을 피하는 것이 좋습니다.
- **이벤트 중복**: 사용자가 조작할 때마다 이벤트가 발생하므로, 같은 동작에 대해 중복 호출이 발생할 수 있습니다. 이 경우 상태를 관리하여 중복 작업을 방지해야 합니다.
- **비디오/오디오 상태**: 미디어가 일시 정지 상태일 때 이 이벤트가 발생하지 않을 수 있으므로, 상태 체크가 필요할 수 있습니다.

## 한 줄 요약
`ontimeupdate` 이벤트는 비디오 및 오디오의 현재 재생 위치가 변경될 때마다 발생하여, 사용자가 미디어의 상태를 실시간으로 확인할 수 있게 돕습니다.