<!--
Meta Description: # JavaScript의 onauxclick: 클릭 이벤트 처리 방법 ## 개요 `onauxclick`는 JavaScript에서 특정 마우스 버튼 클릭을 감지하기 위한 이벤트 속성입니다. 이 이벤트는 주로 브라우저에서 사용자 인터페이스(UI)를 구성할 때 유용하게 사용...
Meta Keywords: onauxclick, button, event, 마우스, 이벤트는
-->

# JavaScript의 onauxclick: 클릭 이벤트 처리 방법

## 개요
`onauxclick`는 JavaScript에서 특정 마우스 버튼 클릭을 감지하기 위한 이벤트 속성입니다. 이 이벤트는 주로 브라우저에서 사용자 인터페이스(UI)를 구성할 때 유용하게 사용됩니다.

## 문서화
### 목적
`onauxclick` 이벤트는 마우스 클릭이 발생했을 때 실행될 함수를 정의할 수 있게 해줍니다. 이 이벤트는 특히 여러 마우스 버튼(예: 마우스 가운데 버튼)로 특정 작업을 수행해야 할 때 유용합니다.

### 사용법
`onauxclick` 이벤트는 HTML 요소에 직접 속성으로 추가하거나 JavaScript에서 이벤트 리스너로 등록하여 사용할 수 있습니다. 이 이벤트는 대부분의 브라우저에서 지원됩니다.

#### HTML에서 사용하기
```html
<button onauxclick="handleAuxClick(event)">여기를 클릭하세요</button>
```

#### JavaScript에서 사용하기
```javascript
const button = document.querySelector('button');
button.onauxclick = function(event) {
    console.log('Aux click detected!');
};
```

## 예제
### 기본 사용 예제
아래는 `onauxclick`을 사용하여 마우스 가운데 버튼 클릭을 감지하는 간단한 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onauxclick 예제</title>
</head>
<body>
    <button onauxclick="handleAuxClick(event)">여기를 클릭하세요</button>
    <script>
        function handleAuxClick(event) {
            if (event.button === 1) { // 가운데 버튼 클릭
                alert('가운데 버튼 클릭이 감지되었습니다!');
            }
        }
    </script>
</body>
</html>
```

## 설명
`onauxclick` 이벤트는 주의해야 할 몇 가지 사항이 있습니다:

1. **브라우저 호환성**: 최신 브라우저에서는 대부분 지원되지만, 구형 브라우저에서는 작동하지 않을 수 있습니다.
2. **이벤트 버튼 코드**: `event.button`을 통해 어떤 버튼이 클릭되었는지 확인할 수 있습니다. 왼쪽 버튼은 0, 가운데 버튼은 1, 오른쪽 버튼은 2입니다.
3. **기본 동작 방지**: 필요에 따라 `event.preventDefault()`를 사용하여 기본 동작을 방지할 수 있습니다.

## 한 줄 요약
`onauxclick`는 JavaScript에서 마우스 가운데 버튼 클릭을 감지하는 이벤트 속성입니다.