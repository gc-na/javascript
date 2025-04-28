<!--
Meta Description: # oncuechange: JavaScript에서의 이벤트 처리 ## 개요 `oncuechange`는 HTML5 비디오와 오디오 요소에 사용되는 이벤트로, 자막이나 캡션의 상태가 변경될 때 발생합니다. 이 이벤트를 통해 개발자는 사용자 인터페이스를 동적으로 업데이트하거...
Meta Keywords: activecues, oncuechange, video, const, videoelement
-->

# oncuechange: JavaScript에서의 이벤트 처리

## 개요
`oncuechange`는 HTML5 비디오와 오디오 요소에 사용되는 이벤트로, 자막이나 캡션의 상태가 변경될 때 발생합니다. 이 이벤트를 통해 개발자는 사용자 인터페이스를 동적으로 업데이트하거나, 자막의 변경 사항에 따라 특정 작업을 수행할 수 있습니다.

## 문서화
`oncuechange` 이벤트는 `<video>` 또는 `<audio>` 요소의 `TextTrack` 객체에 관련된 이벤트로, 자막의 변경이 발생할 때 자동으로 호출됩니다. 이 이벤트는 사용자가 자막을 켜거나 끌 때, 또는 자막의 내용이 동적으로 업데이트될 때 발생합니다.

### 목적
- 자막이 변경될 때 사용자에게 반응하는 인터페이스 제공
- 자막의 내용을 기반으로 추가적인 기능 구현

### 사용법
`oncuechange` 이벤트는 JavaScript에서 다음과 같이 사용됩니다:

```javascript
const videoElement = document.getElementById('myVideo');

videoElement.addEventListener('cuechange', function() {
    const activeCues = this.textTracks[0].activeCues;
    for (let cue of activeCues) {
        console.log(cue.text);
    }
});
```

## 예제
기본 사용 예제를 통해 `oncuechange` 이벤트를 활용하는 방법을 보여줍니다.

### 예제 1: 자막 변경 감지하기
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    <track src="subtitles_en.vtt" kind="subtitles" srclang="en" label="English">
</video>

<script>
    const videoElement = document.getElementById('myVideo');
    
    videoElement.addEventListener('cuechange', function() {
        const activeCues = this.textTracks[0].activeCues;
        if (activeCues.length > 0) {
            console.log('현재 자막:', activeCues[0].text);
        }
    });
</script>
```

### 예제 2: 자막 자동 전환
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    <track src="subtitles_ko.vtt" kind="subtitles" srclang="ko" label="Korean">
</video>

<script>
    const videoElement = document.getElementById('myVideo');
    
    videoElement.addEventListener('cuechange', function() {
        const activeCues = this.textTracks[0].activeCues;
        if (activeCues.length > 0) {
            document.getElementById('subtitleDisplay').innerText = activeCues[0].text;
        }
    });
</script>

<div id="subtitleDisplay"></div>
```

## 설명
`oncuechange` 이벤트를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- `TextTrack` 객체가 브라우저에 의해 지원되어야 하며, 모든 브라우저에서 동일한 방식으로 작동하지 않을 수 있습니다.
- 자막이 없는 경우 `activeCues` 배열은 비어 있습니다.
- 이벤트 핸들러 내에서 `this`는 이벤트가 발생한 요소를 참조합니다.

## 한 줄 요약
`oncuechange` 이벤트는 HTML5 비디오 및 오디오 요소에서 자막의 상태가 변경될 때 발생하여, 동적인 사용자 인터페이스 업데이트를 가능하게 합니다.