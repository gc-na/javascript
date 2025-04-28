<!--
Meta Description: # ondragstart: JavaScript에서 드래그 시작 이벤트 처리하기 ## 개요 `ondragstart`는 HTML 요소가 드래그를 시작할 때 발생하는 이벤트로, JavaScript를 사용하여 사용자 인터페이스에서 드래그 앤 드롭 기능을 구현하는 데 필수적입니...
Meta Keywords: 드래그, ondragstart, event, html, draggable
-->

# ondragstart: JavaScript에서 드래그 시작 이벤트 처리하기

## 개요
`ondragstart`는 HTML 요소가 드래그를 시작할 때 발생하는 이벤트로, JavaScript를 사용하여 사용자 인터페이스에서 드래그 앤 드롭 기능을 구현하는 데 필수적입니다.

## 문서화
`ondragstart` 이벤트는 사용자가 마우스로 요소를 클릭하고 끌기 시작할 때 발생합니다. 이 이벤트는 드래그 가능한 요소에 대해 사용자 정의 동작을 지정할 수 있도록 해줍니다. 

### 사용 목적
- 드래그 앤 드롭 인터페이스를 구축하기 위해 사용됩니다.
- 드래그 시작 시 데이터를 설정하거나 스타일을 변경하는 데 활용됩니다.

### 사용법
`ondragstart`는 HTML 요소에서 이벤트 리스너로 사용되며, JavaScript에서 다음과 같이 설정할 수 있습니다:

```html
<div id="draggable" draggable="true" ondragstart="drag(event)">드래그 해보세요!</div>
```

JavaScript에서 이벤트를 처리하는 방법:
```javascript
function drag(event) {
    event.dataTransfer.setData("text/plain", event.target.id);
}
```

## 예제
기본적인 드래그 시작 이벤트를 구현하는 예제입니다:

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ondragstart 예제</title>
    <style>
        #draggable {
            width: 200px;
            height: 100px;
            background-color: lightblue;
            text-align: center;
            line-height: 100px;
            cursor: move;
        }
    </style>
</head>
<body>

<div id="draggable" draggable="true" ondragstart="drag(event)">드래그 해보세요!</div>

<script>
function drag(event) {
    event.dataTransfer.setData("text/plain", event.target.id);
}
</script>

</body>
</html>
```

## 설명
`ondragstart` 이벤트는 드래그가 시작될 때 호출됩니다. 그러나 이 이벤트를 사용할 때 몇 가지 주의할 점이 있습니다:

- **draggable 속성**: 드래그 가능한 요소에는 반드시 `draggable="true"` 속성을 설정해야 합니다. 이 속성이 없으면 드래그 이벤트가 발생하지 않습니다.
- **dataTransfer 객체**: `event.dataTransfer` 객체를 사용하여 드래그할 데이터 및 유형을 설정해야 합니다. 이를 통해 드래그 앤 드롭 작업을 완료할 수 있습니다.
- **스타일 변경**: 드래그 시작 시 요소의 스타일을 변경할 수 있지만, 드래그가 진행되는 동안 스타일이 유지되어야 합니다.

이벤트 처리를 잘못하면 예기치 않은 동작이 발생할 수 있으므로 주의해야 합니다.

## 한 줄 요약
`ondragstart`는 HTML 요소가 드래그를 시작할 때 발생하는 이벤트로, 드래그 앤 드롭 기능을 구현하는 데 필수적입니다.