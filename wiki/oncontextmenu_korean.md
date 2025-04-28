<!--
Meta Description: # JavaScript의 oncontextmenu: 우클릭 메뉴 이벤트 처리 ## 개요 `oncontextmenu`는 HTML 요소에서 마우스 오른쪽 버튼 클릭 시 발생하는 컨텍스트 메뉴 이벤트를 처리하는 JavaScript의 이벤트 핸들러입니다. 이 이벤트를 사용하여...
Meta Keywords: oncontextmenu, 이벤트, html, 있습니다, 사용자
-->

# JavaScript의 oncontextmenu: 우클릭 메뉴 이벤트 처리

## 개요
`oncontextmenu`는 HTML 요소에서 마우스 오른쪽 버튼 클릭 시 발생하는 컨텍스트 메뉴 이벤트를 처리하는 JavaScript의 이벤트 핸들러입니다. 이 이벤트를 사용하여 사용자 정의 메뉴를 표시하거나 기본 컨텍스트 메뉴의 동작을 방지할 수 있습니다.

## 문서화
### 목적
`oncontextmenu` 이벤트는 사용자가 특정 요소에서 마우스 오른쪽 버튼을 클릭할 때 발생합니다. 이를 통해 웹 개발자는 사용자 경험을 향상시키기 위해 컨텍스트 메뉴를 커스터마이즈하거나 기본 메뉴의 표시를 방지할 수 있습니다.

### 사용법
`oncontextmenu` 이벤트는 HTML 요소에 직접적으로 추가할 수 있으며, JavaScript로도 이벤트 리스너를 설정할 수 있습니다. 아래는 두 가지 방법의 예입니다.

#### HTML 속성으로 사용하기
```html
<div oncontextmenu="return false;">우클릭을 방지하는 텍스트</div>
```

#### JavaScript로 이벤트 리스너 추가하기
```javascript
document.getElementById("myElement").addEventListener("contextmenu", function(event) {
    event.preventDefault(); // 기본 메뉴 방지
    alert("사용자 정의 메뉴를 표시할 수 있습니다.");
});
```

## 예제
### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>oncontextmenu 예제</title>
</head>
<body>
    <div id="myDiv" style="width: 200px; height: 200px; background-color: lightblue;">
        우클릭해 보세요.
    </div>

    <script>
        document.getElementById("myDiv").addEventListener("contextmenu", function(event) {
            event.preventDefault(); // 기본 메뉴 방지
            alert("사용자 정의 메뉴 표시");
        });
    </script>
</body>
</html>
```

## 설명
- **기본 메뉴 방지**: `event.preventDefault()` 메소드를 사용하여 기본 컨텍스트 메뉴의 표시를 방지할 수 있습니다.
- **이벤트 전파**: `oncontextmenu` 이벤트는 버블링이 발생하므로, 부모 요소에도 영향을 미칠 수 있습니다. 필요에 따라 이벤트 전파를 막을 수 있습니다.
- **접근성 고려**: 우클릭 메뉴를 커스터마이즈할 때, 사용자 경험을 고려하여 접근성이 저하되지 않도록 주의해야 합니다.

### 일반적인 실수 및 주의 사항
- **이벤트 리스너 등록 시점**: DOM 요소가 로드되기 전에 이벤트 리스너를 등록하면 해당 요소를 찾을 수 없어 에러가 발생할 수 있습니다. `DOMContentLoaded` 이벤트를 활용하는 것이 좋습니다.
- **브라우저 호환성**: `oncontextmenu`는 대부분의 현대 웹 브라우저에서 지원되지만, 특정 기능이 브라우저에 따라 다를 수 있으므로 테스트가 필요합니다.

## 한 줄 요약
`oncontextmenu`는 HTML 요소에서 마우스 오른쪽 버튼 클릭 시 발생하는 이벤트를 처리하여 사용자 정의 메뉴를 표시하거나 기본 메뉴의 동작을 방지하는 JavaScript의 이벤트 핸들러입니다.