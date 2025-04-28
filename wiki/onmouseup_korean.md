<!--
Meta Description: # JavaScript onmouseup 이벤트: 마우스 버튼 해제 시 발생하는 이벤트 ## 개요 `onmouseup` 이벤트는 사용자가 마우스 버튼을 해제할 때 발생하는 이벤트로, 주로 사용자 인터페이스(UI)에서 상호작용을 처리하는 데 사용됩니다. 이 이벤트는 HT...
Meta Keywords: onmouseup, html, draggable, 마우스, 이벤트는
-->

# JavaScript onmouseup 이벤트: 마우스 버튼 해제 시 발생하는 이벤트

## 개요
`onmouseup` 이벤트는 사용자가 마우스 버튼을 해제할 때 발생하는 이벤트로, 주로 사용자 인터페이스(UI)에서 상호작용을 처리하는 데 사용됩니다. 이 이벤트는 HTML 요소에 바인딩되어 마우스 클릭이 끝났을 때 특정 동작을 실행할 수 있도록 합니다.

## 문서화
### 목적
`onmouseup` 이벤트는 사용자 인터페이스에서 마우스 클릭 종료 시에 특정 작업을 수행할 수 있도록 도와줍니다. 예를 들어, 드래그 앤 드롭 기능을 구현하거나 버튼 클릭 시의 후속 작업을 처리할 때 유용하게 사용됩니다.

### 사용법
`onmouseup` 이벤트는 HTML 요소에 직접 속성으로 설정하거나 JavaScript를 사용하여 이벤트 리스너를 추가하는 방식으로 사용할 수 있습니다.

#### HTML 속성 사용 예:
```html
<button onmouseup="handleMouseUp()">버튼</button>
```

#### JavaScript 사용 예:
```javascript
const button = document.querySelector('button');
button.onmouseup = function() {
    console.log('마우스 버튼이 해제되었습니다.');
};
```

## 예시
다음은 `onmouseup` 이벤트의 기본 사용 예시입니다.

### 예제 1: 버튼 클릭 시 메시지 출력
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>onmouseup 예제</title>
</head>
<body>
    <button onmouseup="alert('버튼에서 마우스를 떼었습니다!')">클릭하세요</button>
</body>
</html>
```

### 예제 2: 드래그 앤 드롭 기능
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>드래그 앤 드롭</title>
    <style>
        #draggable {
            width: 100px;
            height: 100px;
            background-color: blue;
            position: absolute;
        }
    </style>
</head>
<body>
    <div id="draggable"></div>
    <script>
        const draggable = document.getElementById('draggable');
        let offsetX, offsetY;

        draggable.onmousedown = function(e) {
            offsetX = e.clientX - draggable.getBoundingClientRect().left;
            offsetY = e.clientY - draggable.getBoundingClientRect().top;
            document.onmouseup = onMouseUp;
            document.onmousemove = onMouseMove;
        };

        function onMouseMove(e) {
            draggable.style.left = e.clientX - offsetX + 'px';
            draggable.style.top = e.clientY - offsetY + 'px';
        }

        function onMouseUp() {
            document.onmouseup = null;
            document.onmousemove = null;
        }
    </script>
</body>
</html>
```

## 설명
`onmouseup` 이벤트를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **이벤트 버블링**: `onmouseup` 이벤트는 자식 요소에서 발생한 마우스 해제 이벤트가 부모 요소로 전파되는 버블링 현상이 발생합니다. 이로 인해 예상치 못한 동작이 일어날 수 있으므로, 필요에 따라 이벤트 전파를 막아야 할 수 있습니다.
  
- **브라우저 호환성**: 대부분의 최신 브라우저에서 `onmouseup` 이벤트는 지원되지만, 구형 브라우저에서는 일부 기능이 제한될 수 있습니다. 항상 최신 브라우저에서 테스트하는 것이 중요합니다.

- **성능 고려사항**: 많은 요소에 대해 `onmouseup` 이벤트를 바인딩하면 성능에 영향을 미칠 수 있습니다. 이를 피하기 위해 이벤트 위임을 고려하는 것이 좋습니다.

## 한 줄 요약
`onmouseup` 이벤트는 사용자가 마우스 버튼을 해제할 때 발생하여, 사용자 인터페이스의 상호작용을 처리하는 데 유용하다.