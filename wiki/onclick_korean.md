<!--
Meta Description: # JavaScript에서 onclick 이벤트: 기능 및 사용법 ## 개요 `onclick`은 JavaScript에서 HTML 요소에 클릭 이벤트를 처리하기 위해 사용되는 이벤트 속성입니다. 사용자 인터페이스를 더 직관적으로 만들기 위해 버튼 클릭, 링크 선택 등 다...
Meta Keywords: onclick, html, 이벤트, button, javascript에서
-->

# JavaScript에서 onclick 이벤트: 기능 및 사용법

## 개요
`onclick`은 JavaScript에서 HTML 요소에 클릭 이벤트를 처리하기 위해 사용되는 이벤트 속성입니다. 사용자 인터페이스를 더 직관적으로 만들기 위해 버튼 클릭, 링크 선택 등 다양한 사용자 상호작용을 감지하고 반응할 수 있게 합니다.

## 문서화
### 목적
`onclick` 이벤트는 사용자가 HTML 요소를 클릭할 때 실행되는 JavaScript 함수를 지정하는 데 사용됩니다. 이를 통해 웹 페이지의 상호작용을 향상시키고 동적 기능을 추가할 수 있습니다.

### 사용법
`onclick` 속성은 HTML 요소에 직접 추가할 수 있으며, JavaScript 코드 또는 함수 이름을 통해 이벤트 핸들러를 정의할 수 있습니다. 기본 구문은 다음과 같습니다:

```html
<button onclick="functionName()">클릭하세요</button>
```

또는 JavaScript에서 다음과 같이 사용할 수 있습니다:

```javascript
element.onclick = function() {
    // 코드 블록
};
```

### 세부 사항
- `onclick` 이벤트는 모든 HTML 요소에서 사용할 수 있으며, 주로 버튼, 링크, 이미지 등에서 사용됩니다.
- 여러 개의 이벤트 핸들러를 등록할 경우, 마지막으로 등록된 핸들러만 실행됩니다.
- 이벤트 객체를 통해 클릭 이벤트에 대한 추가 정보를 제공받을 수 있습니다.

## 예제
### 기본 사용 예
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>onclick 예제</title>
</head>
<body>
    <button onclick="alert('버튼이 클릭되었습니다!')">클릭하세요</button>
</body>
</html>
```

### JavaScript에서 이벤트 핸들러 등록
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>onclick 예제</title>
</head>
<body>
    <button id="myButton">클릭하세요</button>
    <script>
        document.getElementById("myButton").onclick = function() {
            alert('버튼이 클릭되었습니다!');
        };
    </script>
</body>
</html>
```

## 설명
- **이벤트 중복 등록**: `onclick` 속성을 여러 번 설정하면 마지막에 설정된 값만 유효합니다. 이를 피하기 위해 `addEventListener` 메서드를 사용할 수 있습니다.
- **기본 동작 방지**: 링크 클릭 등 특정 요소의 기본 동작을 방지하려면 `event.preventDefault()`를 사용해야 합니다.
- **this 키워드**: onclick 핸들러 내에서 `this`는 이벤트가 발생한 요소를 참조합니다.

## 한 줄 요약
`onclick`은 JavaScript에서 HTML 요소 클릭 이벤트를 처리하기 위해 사용되는 이벤트 속성으로, 사용자 인터페이스의 상호작용을 향상시키는 데 필수적입니다.