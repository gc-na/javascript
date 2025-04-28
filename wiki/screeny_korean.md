<!--
Meta Description: # JavaScript의 screenY: 스크린 좌표에 대한 이해 ## 개요 `screenY`는 JavaScript에서 마우스 이벤트와 관련된 속성으로, 사용자의 화면 좌표에서 마우스 커서의 Y축 위치를 나타냅니다. 이 속성은 주로 이벤트 핸들링에서 활용되며, 화면의 ...
Meta Keywords: screeny, event, 위치를, 있습니다, 이벤트
-->

# JavaScript의 screenY: 스크린 좌표에 대한 이해

## 개요
`screenY`는 JavaScript에서 마우스 이벤트와 관련된 속성으로, 사용자의 화면 좌표에서 마우스 커서의 Y축 위치를 나타냅니다. 이 속성은 주로 이벤트 핸들링에서 활용되며, 화면의 절대 위치를 기준으로 하여 마우스의 세로 위치를 제공합니다.

## 문서화
### 목적
`screenY`는 사용자가 화면에서 마우스를 움직일 때, 그 위치의 Y좌표를 픽셀 단위로 반환합니다. 이를 통해 웹 개발자는 사용자 인터페이스에서 마우스의 위치에 따라 다양한 동작을 구현할 수 있습니다.

### 사용법
`screenY`는 마우스 이벤트 객체의 속성으로 사용됩니다. 주로 `mousedown`, `mouseup`, `mousemove`와 같은 이벤트 핸들러 내에서 접근하여 사용됩니다.

```javascript
element.addEventListener('mousemove', function(event) {
    console.log(event.screenY);
});
```

### 세부 사항
- `screenY` 값은 브라우저의 화면 좌표계를 기준으로 하며, 화면의 최상단이 0으로 시작합니다.
- 이벤트 객체는 `MouseEvent` 타입이며, 다른 좌표 속성과 함께 사용할 수 있습니다. 예를 들어, `clientY`, `pageY`와 함께 사용하여 다양한 좌표 값을 비교하고 활용할 수 있습니다.
- `screenY`는 읽기 전용 속성으로, 값을 직접 수정할 수 없습니다.

## 예제
### 기본 사용 예제
```javascript
document.addEventListener('mousemove', function(event) {
    console.log('Mouse Y Position on Screen: ' + event.screenY);
});
```

### 클릭 이벤트에서의 사용
```javascript
document.addEventListener('click', function(event) {
    alert('You clicked at Y position: ' + event.screenY);
});
```

## 설명
### 일반적인 함정 및 주의 사항
- `screenY`는 뷰포트나 스크롤에 영향을 받지 않기 때문에, 스크롤된 위치와는 무관하게 화면상의 픽셀 위치를 제공합니다.
- 다양한 브라우저와 화면 해상도에서 `screenY`의 값이 일관되게 나타나지만, 여러 모니터 환경에서는 각 모니터의 위치와 해상도에 따라 값이 달라질 수 있습니다.
- 이벤트가 발생하는 요소의 위치에 따라 `screenY`가 예상과 다르게 동작할 수 있으므로, 필요 시 추가적인 계산을 통해 사용해야 할 수 있습니다.

## 한줄 요약
`screenY`는 JavaScript에서 마우스의 Y축 위치를 화면 좌표 기준으로 반환하는 속성입니다.