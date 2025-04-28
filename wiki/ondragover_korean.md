<!--
Meta Description: # JavaScript의 ondragover: 드래그 앤 드롭 이벤트 처리 ## 개요 `ondragover`는 HTML 요소에서 드래그된 객체가 해당 요소 위에 있을 때 발생하는 이벤트입니다. 이 이벤트는 드래그 앤 드롭 기능을 구현할 때 중요한 역할을 하며, 사용자가...
Meta Keywords: ondragover, event, html, 드래그된, 이벤트는
-->

# JavaScript의 ondragover: 드래그 앤 드롭 이벤트 처리

## 개요
`ondragover`는 HTML 요소에서 드래그된 객체가 해당 요소 위에 있을 때 발생하는 이벤트입니다. 이 이벤트는 드래그 앤 드롭 기능을 구현할 때 중요한 역할을 하며, 사용자가 드래그한 내용을 수용할 수 있는지 여부를 브라우저에 알려줍니다.

## 문서화
### 목적
`ondragover` 이벤트는 사용자가 드래그한 요소가 특정 영역 위에 있을 때 실행됩니다. 이 이벤트는 기본적으로 드롭 가능 여부를 제어하는 데 사용되며, 개발자는 이 이벤트를 통해 드래그된 요소를 수용할 수 있는 영역을 사용자에게 시각적으로 알려줄 수 있습니다.

### 사용법
`ondragover` 이벤트는 HTML 요소에 직접적으로 추가하거나 JavaScript를 통해 핸들러를 설정할 수 있습니다. 기본적으로 이 이벤트는 드래그가 진행되는 동안 지속적으로 호출됩니다.

```html
<div id="drop-area" ondragover="allowDrop(event)">여기에 드래그해 주세요</div>
```

### 세부사항
- **이벤트 객체**: `ondragover` 이벤트 핸들러에서 이벤트 객체는 자동으로 전달됩니다. 이 객체를 사용하여 기본 동작을 방지하고 드롭 가능 상태를 설정할 수 있습니다.
- **기본 동작 방지**: 드래그된 객체가 드롭되기 위해서는 `event.preventDefault()` 메소드를 호출해야 합니다. 그렇지 않으면 드롭 이벤트가 발생하지 않습니다.

## 예제
### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Drag and Drop Example</title>
    <style>
        #drop-area {
            width: 300px;
            height: 200px;
            border: 2px dashed #ccc;
            text-align: center;
            line-height: 200px;
        }
    </style>
</head>
<body>

<div id="drop-area" ondragover="allowDrop(event)" ondrop="drop(event)">여기에 파일을 드롭하세요</div>

<script>
function allowDrop(event) {
    event.preventDefault(); // 기본 동작 방지
}

function drop(event) {
    event.preventDefault();
    // 드롭된 파일 처리 로직 추가
}
</script>

</body>
</html>
```

## 설명
`ondragover` 이벤트를 사용할 때 주의해야 할 점은 다음과 같습니다:
- **기본 동작**: 드래그된 객체가 드롭되는 것을 허용하기 위해서는 반드시 `event.preventDefault()`를 호출해야 합니다. 이를 호출하지 않으면 드롭 이벤트가 발생하지 않습니다.
- **스타일 변경**: 드래그된 객체가 드랍 영역 위에 있을 때 시각적 피드백을 제공하기 위해 CSS 스타일을 변경하는 것이 좋습니다. 예를 들어, 배경색을 변경하여 사용자가 드롭할 수 있는 위치임을 알릴 수 있습니다.

## 한 줄 요약
`ondragover` 이벤트는 HTML 요소 위에 드래그된 객체가 있을 때 발생하며, 드롭 가능 여부를 제어하는 데 사용됩니다.