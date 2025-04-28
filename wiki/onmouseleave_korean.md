<!--
Meta Description: # JavaScript의 onmouseleave 이벤트에 대한 완벽 가이드 ## 개요 `onmouseleave` 이벤트는 사용자가 마우스를 HTML 요소의 영역에서 벗어날 때 발생하는 JavaScript 이벤트입니다. 이 이벤트는 주로 UI/UX 개선을 위해 요소의 상...
Meta Keywords: onmouseleave, html, 이벤트는, 요소의, div
-->

# JavaScript의 onmouseleave 이벤트에 대한 완벽 가이드

## 개요
`onmouseleave` 이벤트는 사용자가 마우스를 HTML 요소의 영역에서 벗어날 때 발생하는 JavaScript 이벤트입니다. 이 이벤트는 주로 UI/UX 개선을 위해 요소의 상태를 변경하거나 애니메이션을 트리거하는 데 사용됩니다.

## 문서화
### 목적
`onmouseleave` 이벤트는 사용자가 마우스를 특정 요소에서 이동할 때 발생하여, 사용자 인터랙션에 따라 동적인 반응을 구현할 수 있게 해줍니다.

### 사용법
`onmouseleave` 이벤트는 HTML 요소에 직접적으로 할당할 수 있으며, JavaScript 코드에서 이벤트 리스너를 추가하여 사용할 수 있습니다.

#### HTML 요소에 직접 할당
```html
<div onmouseleave="myFunction()">이 요소에서 마우스를 빼세요!</div>
```

#### JavaScript에서 이벤트 리스너 추가
```javascript
const element = document.getElementById('myElement');
element.addEventListener('mouseleave', function() {
    // 이벤트가 발생했을 때 수행할 작업
});
```

### 세부 사항
- 이벤트는 마우스가 요소의 경계를 완전히 넘어서야 발생합니다.
- `onmouseleave`는 `onmouseout`과 유사하지만, `onmouseout`은 자식 요소로 마우스가 이동할 때도 발생할 수 있습니다. 반면, `onmouseleave`는 오직 부모 요소에서 마우스가 벗어날 때만 발생합니다.
- 이 이벤트는 일반적으로 CSS 스타일 변경, 애니메이션 종료, 또는 기타 사용자 피드백을 제공하기 위해 사용됩니다.

## 예제
### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onmouseleave 예제</title>
    <style>
        #myElement {
            width: 200px;
            height: 200px;
            background-color: lightblue;
            text-align: center;
            line-height: 200px;
            transition: background-color 0.5s;
        }
    </style>
</head>
<body>
    <div id="myElement" onmouseleave="changeColor()">마우스를 뺴세요!</div>

    <script>
        function changeColor() {
            document.getElementById('myElement').style.backgroundColor = 'lightcoral';
        }
    </script>
</body>
</html>
```

### JavaScript에서 이벤트 리스너 사용
```html
<div id="myElement">마우스를 뺴세요!</div>

<script>
    const element = document.getElementById('myElement');
    element.addEventListener('mouseleave', function() {
        this.style.backgroundColor = 'lightcoral';
    });
</script>
```

## 설명
- `onmouseleave` 이벤트는 마우스가 요소를 떠날 때만 발생하기 때문에, 자식 요소로의 이동과는 관련이 없습니다. 이로 인해 UI 요소의 상태를 명확하게 제어할 수 있습니다.
- 이벤트가 발생하지 않는 경우, 요소의 경계를 정확하게 정의하고, 자식 요소가 없도록 확인해야 합니다.
- 브라우저의 호환성에 따라 동작이 다를 수 있으므로, 다양한 브라우저에서 테스트하는 것이 좋습니다.

## 한 줄 요약
`onmouseleave` 이벤트는 사용자가 HTML 요소의 경계를 벗어날 때 발생하여, 동적 사용자 인터랙션을 가능하게 합니다.