<!--
Meta Description: # JavaScript의 ondragend 이벤트: 드래그 앤 드롭의 끝내기 ## 개요 `ondragend`는 사용자가 드래그 앤 드롭 작업을 마칠 때 발생하는 이벤트입니다. 이 이벤트는 드래그된 요소가 드롭 영역에서 놓이거나 드래그가 취소되었을 때 트리거됩니다. Ja...
Meta Keywords: 드래그, ondragend, 있습니다, draggable, html
-->

# JavaScript의 ondragend 이벤트: 드래그 앤 드롭의 끝내기

## 개요
`ondragend`는 사용자가 드래그 앤 드롭 작업을 마칠 때 발생하는 이벤트입니다. 이 이벤트는 드래그된 요소가 드롭 영역에서 놓이거나 드래그가 취소되었을 때 트리거됩니다. JavaScript에서 `ondragend`를 활용하면 드래그 작업의 완료 상태를 감지하고 이에 대한 처리를 할 수 있습니다.

## 문서화
### 목적
`ondragend` 이벤트는 HTML 요소가 드래그 작업을 완료했을 때 발생합니다. 이를 통해 사용자는 드래그 완료 후의 UI 업데이트나 데이터 처리를 수행할 수 있습니다.

### 사용법
`ondragend`는 HTML 요소에 직접 이벤트 핸들러를 추가하거나 JavaScript를 통해 동적으로 설정할 수 있습니다. 이벤트 리스너는 `addEventListener` 메서드를 사용하여 등록할 수 있습니다.

```html
<div id="draggable" draggable="true">드래그하세요!</div>
```

```javascript
const draggableElement = document.getElementById('draggable');

draggableElement.ondragend = function(event) {
    console.log('드래그가 끝났습니다.');
};
```

또는 `addEventListener`를 사용할 수 있습니다:

```javascript
draggableElement.addEventListener('dragend', function(event) {
    console.log('드래그가 끝났습니다.');
});
```

## 예제
### 기본 사용 예제
다음은 드래그 가능한 요소를 만들고, 드래그가 끝났을 때 메시지를 출력하는 간단한 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ondragend 예제</title>
    <style>
        #draggable {
            width: 100px;
            height: 100px;
            background-color: lightblue;
            cursor: move;
        }
    </style>
</head>
<body>
    <div id="draggable" draggable="true">드래그하세요!</div>

    <script>
        const draggableElement = document.getElementById('draggable');

        draggableElement.ondragend = function(event) {
            console.log('드래그가 끝났습니다.');
        };
    </script>
</body>
</html>
```

## 설명
`ondragend` 이벤트를 사용할 때 주의할 점은 드래그 완료 후의 상태를 적절하게 처리하는 것입니다. 예를 들어, 드래그한 요소를 다른 위치에 놓지 않는다면, 이를 처리하는 로직이 필요할 수 있습니다. 또한, 드래그 중에 발생하는 다른 이벤트(`dragstart`, `drag`, `drop`)와의 상호작용도 고려해야 합니다.

### 일반적인 함정 및 주의 사항
- **드래그 가능 여부**: `draggable` 속성이 `true`로 설정된 요소만 드래그할 수 있습니다.
- **이벤트 전파**: 드래그 이벤트는 다른 이벤트와 마찬가지로 이벤트 전파를 따릅니다. 필요한 경우 `event.stopPropagation()`을 사용할 수 있습니다.
- **한 번의 드래그**: `ondragend`는 드래그가 끝날 때마다 호출되므로, 여러 번 드래그 작업을 수행할 수 있는 요소에서 상태를 관리해야 합니다.

## 한 줄 요약
`ondragend` 이벤트는 드래그 앤 드롭 작업이 완료되었을 때 발생하며, 이를 통해 드래그 종료 후의 처리를 수행할 수 있습니다.