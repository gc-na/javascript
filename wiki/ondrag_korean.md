<!--
Meta Description: # JavaScript의 ondrag 이벤트: 드래그 앤 드롭 기능 구현하기 ## 개요 `ondrag`는 HTML5의 드래그 앤 드롭 API의 일부로, 사용자가 요소를 드래그할 때 발생하는 이벤트입니다. 이 이벤트를 사용하면 웹 애플리케이션에서 사용자 인터랙션을 향상시...
Meta Keywords: 드래그, ondrag, draggable, 이벤트는, 이벤트
-->

# JavaScript의 ondrag 이벤트: 드래그 앤 드롭 기능 구현하기

## 개요
`ondrag`는 HTML5의 드래그 앤 드롭 API의 일부로, 사용자가 요소를 드래그할 때 발생하는 이벤트입니다. 이 이벤트를 사용하면 웹 애플리케이션에서 사용자 인터랙션을 향상시키고, 요소를 이동하거나 복사하는 등의 기능을 쉽게 구현할 수 있습니다.

## 문서화
`ondrag` 이벤트는 사용자가 마우스 버튼을 누른 채로 요소를 끌고 이동하는 동안 발생합니다. 이 이벤트는 주로 드래그 가능한 요소에 추가되어야 하며, 이와 관련된 다른 이벤트(`ondragstart`, `ondragover`, `ondrop` 등)와 함께 활용됩니다.

### 목적
`ondrag` 이벤트는 사용자가 드래그하는 동안 특정 작업을 수행할 수 있게 해주며, 드래그 앤 드롭 기능을 구현하는 데 필수적입니다.

### 사용법
`ondrag` 이벤트는 HTML 요소에 직접 속성으로 추가하거나, JavaScript를 통해 이벤트 리스너를 등록하여 사용할 수 있습니다.

```html
<div id="draggable" draggable="true" ondrag="drag(event)">드래그 할 요소</div>
```

또는 JavaScript를 사용하여:

```javascript
const draggableElement = document.getElementById('draggable');
draggableElement.addEventListener('drag', function(event) {
    // 드래그 중 수행할 작업
});
```

## 예제
기본적인 드래그 이벤트 사용 예제는 다음과 같습니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>드래그 이벤트 예제</title>
    <style>
        #draggable {
            width: 100px;
            height: 100px;
            background-color: lightblue;
            border: 1px solid #000;
        }
    </style>
</head>
<body>
    <div id="draggable" draggable="true" ondrag="drag(event)">드래그 할 요소</div>

    <script>
        function drag(event) {
            console.log("드래그 중입니다!");
        }
    </script>
</body>
</html>
```

### 설명
- 드래그 가능한 요소에는 `draggable` 속성을 `true`로 설정해야 합니다.
- `ondrag` 이벤트는 사용자가 마우스를 움직이는 동안 반복적으로 발생하므로, 성능에 유의해야 합니다.
- 이벤트 핸들러에서는 `event` 객체를 통해 드래그 중인 데이터와 관련된 정보를 얻을 수 있습니다.

### 일반적인 실수 및 주의 사항
- `draggable` 속성을 설정하지 않으면 `ondrag` 이벤트가 발생하지 않습니다.
- `ondrag` 이벤트는 드래그가 시작된 후에만 발생하므로, `ondragstart` 이벤트와 함께 사용하여 드래그 시작 시 필요한 작업을 수행하는 것이 좋습니다.
- 드래그 중에 스타일을 변경하거나 DOM을 조작하는 경우 성능 저하가 있을 수 있으므로 주의해야 합니다.

## 한 줄 요약
`ondrag` 이벤트는 드래그 앤 드롭 기능을 구현할 때 사용자가 요소를 드래그하는 동안 발생하는 이벤트입니다.