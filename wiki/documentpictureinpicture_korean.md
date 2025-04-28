<!--
Meta Description: # DocumentPictureInPicture: 자바스크립트에서의 PIP 기능 활용하기 ## 개요 `DocumentPictureInPicture`는 자바스크립트를 사용하여 브라우저에서 Picture-in-Picture(PIP) 모드를 구현하는 기능입니다. 이 기능을 ...
Meta Keywords: pip, video, 비디오, 비디오를, 모드를
-->

# DocumentPictureInPicture: 자바스크립트에서의 PIP 기능 활용하기

## 개요
`DocumentPictureInPicture`는 자바스크립트를 사용하여 브라우저에서 Picture-in-Picture(PIP) 모드를 구현하는 기능입니다. 이 기능을 통해 사용자는 비디오 콘텐츠를 다른 작업을 수행하는 동안도 계속 시청할 수 있습니다.

## 문서화
### 목적
`DocumentPictureInPicture`는 사용자가 비디오를 PIP 모드로 전환하여, 화면의 작은 창에서 비디오를 재생할 수 있도록 도와줍니다. 이 기능은 멀티태스킹을 지원하며 사용자 경험을 향상시킵니다.

### 사용법
PIP 모드는 HTML5 비디오 요소와 함께 작동하며, 자바스크립트를 통해 제어됩니다. 다음은 기본적인 사용 방법입니다.

1. HTML 문서에서 비디오 요소를 추가합니다.
2. 비디오 요소에 PIP 모드를 적용할 수 있는 버튼을 생성합니다.
3. 자바스크립트를 사용하여 버튼 클릭 시 비디오를 PIP 모드로 전환합니다.

### 세부사항
- **지원 브라우저**: PIP 기능은 최신 버전의 Chrome, Firefox, Edge 등에서 지원됩니다. Safari는 특정 조건에서만 지원합니다.
- **비디오 요소**: `<video>` 태그를 사용하여 비디오를 삽입해야 하며, PIP 모드는 비디오가 재생 중일 때만 활성화됩니다.
- **사용자 상호작용**: PIP 모드 전환은 사용자 상호작용(예: 버튼 클릭) 없이는 자동으로 수행되지 않습니다.

## 예제
다음은 비디오를 PIP 모드로 전환하는 간단한 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PIP 예제</title>
</head>
<body>
    <video id="video" width="400" controls>
        <source src="video.mp4" type="video/mp4">
        브라우저가 비디오 태그를 지원하지 않습니다.
    </video>
    <button id="pipButton">PIP 모드 전환</button>

    <script>
        const video = document.getElementById('video');
        const pipButton = document.getElementById('pipButton');

        pipButton.addEventListener('click', async () => {
            if (document.pictureInPictureElement) {
                await document.exitPictureInPicture();
            } else {
                await video.requestPictureInPicture();
            }
        });
    </script>
</body>
</html>
```

## 설명
PIP 모드를 사용할 때 주의해야 할 몇 가지 사항이 있습니다.

- **브라우저 호환성**: 모든 브라우저가 PIP 모드를 지원하는 것은 아닙니다. 사용자가 사용하는 브라우저의 지원 여부를 확인해야 합니다.
- **비디오 상태**: 비디오는 반드시 재생 중이어야 PIP 모드로 전환할 수 있습니다. 정지 상태에서는 전환이 불가능합니다.
- **사용자 인터페이스**: PIP 모드는 사용자에게 비디오를 쉽게 조작할 수 있는 UI를 제공합니다. 사용자는 언제든지 PIP 모드를 종료할 수 있습니다.

## 한 줄 요약
`DocumentPictureInPicture`는 자바스크립트를 통해 웹 비디오 콘텐츠를 Picture-in-Picture 모드로 전환할 수 있는 기능입니다.