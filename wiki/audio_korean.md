<!--
Meta Description: # JavaScript에서의 오디오 (Audio): 웹에서 오디오 재생의 기초 및 활용 ## 개요 JavaScript의 오디오 기능은 웹 애플리케이션에서 오디오 파일을 재생하고 조작할 수 있는 강력한 도구입니다. 이 기능은 HTML5의 `<audio>` 요소와 함께 사...
Meta Keywords: 오디오, audio, 있습니다, javascript의, 기능은
-->

# JavaScript에서의 오디오 (Audio): 웹에서 오디오 재생의 기초 및 활용

## 개요
JavaScript의 오디오 기능은 웹 애플리케이션에서 오디오 파일을 재생하고 조작할 수 있는 강력한 도구입니다. 이 기능은 HTML5의 `<audio>` 요소와 함께 사용되며, 다양한 오디오 형식을 지원합니다. 이 문서에서는 JavaScript를 사용하여 오디오를 재생하는 방법과 관련된 핵심 개념을 다룹니다.

## 문서화

### 목적
JavaScript의 오디오 기능은 개발자가 웹 애플리케이션에 음악이나 효과음을 쉽게 통합할 수 있도록 해줍니다. 이는 사용자 경험을 향상시키고, 인터랙티브한 웹사이트를 만드는 데 필수적입니다.

### 사용법
오디오를 재생하려면 HTML의 `<audio>` 요소와 JavaScript API를 사용하여 오디오 파일을 로드하고 제어할 수 있습니다. 기본적인 사용법은 다음과 같습니다:

1. HTML에서 `<audio>` 요소를 생성합니다.
2. JavaScript를 사용하여 오디오 요소에 접근하고 메서드를 호출하여 재생, 일시 정지, 멈춤 등의 기능을 구현합니다.

### 세부 사항
- **오디오 형식**: 일반적으로 지원되는 오디오 형식은 MP3, WAV, Ogg 등이 있습니다.
- **속성**:
  - `src`: 재생할 오디오 파일의 URL.
  - `controls`: 기본 재생 컨트롤을 표시합니다.
  - `autoplay`: 페이지 로드 시 자동 재생합니다.
  - `loop`: 오디오가 끝난 후 자동으로 반복합니다.
  
- **메서드**:
  - `play()`: 오디오 재생 시작.
  - `pause()`: 오디오 일시 정지.
  - `currentTime`: 현재 재생 시간을 설정하거나 가져옵니다.
  
- **이벤트**: 다양한 이벤트를 통해 오디오 재생 상태를 감지할 수 있습니다. 예를 들어, `ended` 이벤트는 오디오가 끝났을 때 발생합니다.

## 예제

### 기본 오디오 재생
```html
<audio id="myAudio" src="audio/sample.mp3" controls></audio>
<script>
    const audio = document.getElementById('myAudio');
    audio.play(); // 오디오 재생 시작
</script>
```

### 재생 및 일시 정지 버튼 추가
```html
<audio id="myAudio" src="audio/sample.mp3"></audio>
<button onclick="playAudio()">재생</button>
<button onclick="pauseAudio()">일시 정지</button>

<script>
    const audio = document.getElementById('myAudio');

    function playAudio() {
        audio.play();
    }

    function pauseAudio() {
        audio.pause();
    }
</script>
```

## 설명
JavaScript의 오디오 기능을 사용할 때 몇 가지 일반적인 함정이 있습니다. 예를 들어, 사용자가 직접 상호작용하지 않으면 자동 재생이 차단될 수 있습니다. 이로 인해 `autoplay` 속성이 무시될 수 있으므로, 오디오 파일을 재생하기 전에 사용자의 클릭 이벤트를 요구하는 것이 좋습니다. 또한, 다양한 브라우저에서 오디오 형식의 호환성에 유의해야 합니다.

## 한 줄 요약
JavaScript의 오디오 기능은 웹 애플리케이션에서 오디오 파일을 재생하고 조작할 수 있는 강력한 도구입니다.