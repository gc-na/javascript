<!--
Meta Description: # JavaScript의 screenX: 화면 좌표를 얻는 방법 ## 개요 `screenX`는 JavaScript에서 브라우저의 화면 좌표를 가져오는 데 사용되는 속성으로, 주로 이벤트 객체에서 사용됩니다. 이 속성은 마우스 이벤트가 발생한 위치의 화면 내 좌표를 픽셀...
Meta Keywords: screenx, event, 위치의, 화면의, 좌표를
-->

# JavaScript의 screenX: 화면 좌표를 얻는 방법

## 개요
`screenX`는 JavaScript에서 브라우저의 화면 좌표를 가져오는 데 사용되는 속성으로, 주로 이벤트 객체에서 사용됩니다. 이 속성은 마우스 이벤트가 발생한 위치의 화면 내 좌표를 픽셀 단위로 반환합니다.

## 문서화
### 목적
`screenX`는 사용자의 화면에서 마우스 이벤트가 발생한 정확한 위치를 알기 위해 사용됩니다. 이 속성은 특히 드래그 앤 드롭 인터페이스나 사용자 상호작용을 이해하는 데 유용합니다.

### 사용법
`screenX`는 주로 마우스 이벤트 객체 내에서 접근할 수 있습니다. 이벤트 객체는 다양한 이벤트 처리기에서 자동으로 전달됩니다. 예를 들어, 클릭 이벤트가 발생했을 때 해당 위치의 `screenX` 값을 확인할 수 있습니다.

```javascript
element.addEventListener('click', function(event) {
    console.log(event.screenX);
});
```

### 세부 사항
- `screenX`는 브라우저의 화면 좌표계에서의 X축 위치를 나타내며, 화면의 왼쪽 가장자리에서 시작하여 오른쪽으로 이동하면서 값이 증가합니다.
- 이 값은 전체 화면의 픽셀 단위로 반환되며, 모니터의 해상도와 관계없이 일관된 값을 제공합니다.
- `screenX` 속성은 읽기 전용입니다. 값을 변경할 수 없습니다.

## 예제
### 기본 사용 예제
아래 코드는 마우스 클릭 시 화면의 X좌표를 콘솔에 출력하는 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>screenX 예제</title>
</head>
<body>
    <button id="myButton">클릭하세요</button>
    <script>
        document.getElementById('myButton').addEventListener('click', function(event) {
            alert('클릭한 위치의 screenX: ' + event.screenX);
        });
    </script>
</body>
</html>
```

### 드래그 앤 드롭 예제
아래 예제는 드래그 앤 드롭 이벤트에서 `screenX`를 활용하는 방법을 보여줍니다.

```javascript
const draggable = document.getElementById('draggable');

draggable.addEventListener('dragstart', function(event) {
    console.log('드래그 시작 위치의 screenX:', event.screenX);
});

draggable.addEventListener('dragend', function(event) {
    console.log('드래그 종료 위치의 screenX:', event.screenX);
});
```

## 설명
- `screenX`는 화면의 픽셀 좌표를 기반으로 하기 때문에 스크롤이나 확대/축소 상태와는 무관하게 항상 동일한 좌표를 제공합니다.
- `screenX`는 브라우저의 주소 표시줄이나 시스템의 인터페이스와 같은 요소에 의해 영향을 받지 않기 때문에, 화면의 실제 위치를 정확히 반영합니다.
- 그러나 모바일 기기에서는 화면의 물리적인 크기나 해상도에 따라 다르게 나타날 수 있으므로 주의가 필요합니다.

## 한 줄 요약
`screenX`는 JavaScript에서 마우스 이벤트 발생 위치의 화면 내 X좌표를 픽셀 단위로 반환하는 속성입니다.