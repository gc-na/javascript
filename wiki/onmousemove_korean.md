<!--
Meta Description: # JavaScript onmousemove 이벤트: 마우스 이동 감지하기 ## 개요 `onmousemove`는 사용자의 마우스가 요소 위를 이동할 때 발생하는 이벤트를 처리하기 위해 JavaScript에서 사용되는 이벤트 핸들러입니다. 이 이벤트를 활용하면 웹 페이지...
Meta Keywords: onmousemove, 있습니다, html, event, 마우스가
-->

# JavaScript onmousemove 이벤트: 마우스 이동 감지하기

## 개요
`onmousemove`는 사용자의 마우스가 요소 위를 이동할 때 발생하는 이벤트를 처리하기 위해 JavaScript에서 사용되는 이벤트 핸들러입니다. 이 이벤트를 활용하면 웹 페이지에서 사용자 상호작용을 더욱 풍부하게 만들 수 있습니다.

## 문서화
### 목적
`onmousemove` 이벤트는 마우스가 특정 HTML 요소 안에서 움직일 때마다 호출됩니다. 이를 통해 사용자의 마우스 위치를 감지하고, 실시간으로 반응하는 웹 페이지를 만들 수 있습니다.

### 사용법
`onmousemove` 이벤트는 HTML 요소에 직접 설정하거나 JavaScript를 통해 동적으로 추가할 수 있습니다. 다음은 기본 구문입니다:

```html
<element onmousemove="myFunction(event)">...</element>
```

또는 JavaScript를 사용하여 이벤트 리스너를 추가할 수 있습니다:

```javascript
element.addEventListener("mousemove", myFunction);
```

### 세부 사항
- `event` 객체는 `onmousemove` 이벤트가 발생할 때 자동으로 전달되며, 마우스의 현재 위치를 포함한 정보가 담겨 있습니다.
- 주요 속성으로는 `clientX`, `clientY`, `screenX`, `screenY`가 있으며, 각각 마우스의 X, Y 좌표를 제공합니다.

## 예제
다음은 `onmousemove` 이벤트를 활용한 기본적인 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>onmousemove 예제</title>
    <style>
        #myDiv {
            width: 400px;
            height: 400px;
            border: 1px solid black;
            position: relative;
        }
    </style>
</head>
<body>
    <div id="myDiv" onmousemove="showCoordinates(event)"></div>
    <p id="coordinates"></p>

    <script>
        function showCoordinates(event) {
            const x = event.clientX;
            const y = event.clientY;
            document.getElementById('coordinates').innerText = `X: ${x}, Y: ${y}`;
        }
    </script>
</body>
</html>
```

위 예제에서, 마우스가 `myDiv` 요소 위를 이동할 때마다 현재 마우스 위치가 화면에 표시됩니다.

## 설명
- **공통적인 함정**: 마우스가 요소의 경계를 넘어갈 때 `onmousemove` 이벤트가 발생하지 않기 때문에, 요소의 크기를 적절히 설정해야 합니다.
- **퍼포먼스**: `onmousemove` 이벤트는 매우 빈번하게 발생하므로, 성능에 영향을 줄 수 있습니다. 특히, 복잡한 작업을 수행하는 경우 `requestAnimationFrame`이나 `throttle` 함수를 사용하여 성능을 개선할 수 있습니다.
- **브라우저 호환성**: 대부분의 최신 브라우저에서 지원되지만, 구형 브라우저에서는 다르게 동작할 수 있으니 주의가 필요합니다.

## 한 줄 요약
`onmousemove` 이벤트는 웹 페이지에서 마우스의 이동을 실시간으로 감지하고 반응할 수 있도록 도와주는 JavaScript 이벤트입니다.