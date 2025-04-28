<!--
Meta Description: # onmousewheel: JavaScript에서 마우스 휠 이벤트 처리하기 ## 개요 `onmousewheel`은 JavaScript에서 마우스 휠의 움직임을 감지하고 처리하기 위한 이벤트 핸들러입니다. 이 이벤트는 사용자가 마우스를 위아래로 스크롤할 때 발생하며,...
Meta Keywords: 스크롤, onmousewheel, 이벤트, 있습니다, html
-->

# onmousewheel: JavaScript에서 마우스 휠 이벤트 처리하기

## 개요
`onmousewheel`은 JavaScript에서 마우스 휠의 움직임을 감지하고 처리하기 위한 이벤트 핸들러입니다. 이 이벤트는 사용자가 마우스를 위아래로 스크롤할 때 발생하며, 페이지 내의 요소에 대한 사용자 인터랙션을 향상시키는 데 유용합니다.

## 문서화
### 목적
`onmousewheel` 이벤트는 사용자가 마우스 휠을 굴릴 때 발생하며, 이를 통해 다양한 사용자 경험을 개선하고, 스크롤 동작을 제어할 수 있습니다.

### 사용법
`onmousewheel` 이벤트는 HTML 요소에 직접 설정할 수 있으며, 이를 통해 특정 요소에서 스크롤 이벤트를 감지하고 처리할 수 있습니다.

```javascript
element.onmousewheel = function(event) {
    // 이벤트 처리 코드
};
```

### 세부사항
- **이벤트 객체**: `onmousewheel` 이벤트가 발생할 때, 이벤트 객체가 인자로 전달됩니다. 이 객체는 `deltaY` 속성을 통해 휠의 이동 방향과 양을 알 수 있습니다.
- **브라우저 호환성**: `onmousewheel`은 대부분의 웹 브라우저에서 지원되지만, 최신 웹 표준에서는 `wheel` 이벤트 사용이 권장됩니다.
- **스크롤 방향**: `deltaY`가 양수일 경우 아래로 스크롤, 음수일 경우 위로 스크롤을 의미합니다.

## 예제
### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>onmousewheel 예제</title>
</head>
<body>
    <div id="scrollable" style="height: 200px; overflow: auto;">
        <p>스크롤 가능한 내용...</p>
        <p>스크롤 가능한 내용...</p>
        <p>스크롤 가능한 내용...</p>
        <p>스크롤 가능한 내용...</p>
        <p>스크롤 가능한 내용...</p>
    </div>

    <script>
        const scrollableDiv = document.getElementById('scrollable');
        scrollableDiv.onmousewheel = function(event) {
            console.log('휠 스크롤:', event.deltaY);
        };
    </script>
</body>
</html>
```

## 설명
### 일반적인 문제 및 주의 사항
- **브라우저 차이**: 모든 브라우저가 `onmousewheel`을 동일하게 처리하지 않을 수 있습니다. 크로스 브라우저 호환성을 고려하여 `wheel` 이벤트를 사용하는 것이 좋습니다.
- **이벤트 전파**: `onmousewheel` 이벤트가 발생하면, 이를 다른 이벤트와 결합하여 사용하면 예기치 않은 동작이 발생할 수 있습니다. 필요에 따라 `event.preventDefault()`를 사용하여 기본 스크롤 동작을 방지할 수 있습니다.
- **성능 문제**: 대량의 데이터가 스크롤 될 때 이벤트가 계속 발생하므로, 성능 저하를 피하기 위해 사용 시 디바운스(debounce) 기술을 도입하는 것이 좋습니다.

## 한 줄 요약
`onmousewheel`은 JavaScript에서 마우스 휠 스크롤 이벤트를 처리하는 데 사용되는 이벤트 핸들러입니다.