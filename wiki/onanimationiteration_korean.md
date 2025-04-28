<!--
Meta Description: # onanimationiteration: JavaScript 애니메이션 이벤트 처리 ## 개요 `onanimationiteration`은 JavaScript에서 CSS 애니메이션이 반복될 때 발생하는 이벤트를 처리하는 속성입니다. 이 이벤트는 애니메이션이 한 사이클을...
Meta Keywords: 애니메이션이, 이벤트, onanimationiteration, css, html
-->

# onanimationiteration: JavaScript 애니메이션 이벤트 처리

## 개요
`onanimationiteration`은 JavaScript에서 CSS 애니메이션이 반복될 때 발생하는 이벤트를 처리하는 속성입니다. 이 이벤트는 애니메이션이 한 사이클을 완료한 후 다시 시작할 때 호출됩니다.

## 문서화
### 목적
`onanimationiteration` 이벤트는 CSS 애니메이션의 반복을 감지하고, 그에 따른 특정 행동을 수행할 수 있도록 도와줍니다. 주로 사용자 인터페이스(UI)에서 애니메이션의 반복 동작에 따라 추가적인 로직을 실행할 때 사용됩니다.

### 사용법
`onanimationiteration`은 HTML 요소의 JavaScript 속성으로 설정할 수 있으며, 이벤트 리스너를 추가하여 애니메이션 반복 시 특정 함수를 호출할 수 있습니다.

### 세부사항
- **이벤트 트리거**: CSS 애니메이션이 한 사이클을 완료하고 다시 시작할 때 발생합니다.
- **이벤트 객체**: 이벤트 핸들러에는 `AnimationEvent` 객체가 전달되며, 이 객체를 통해 애니메이션의 정보(예: 애니메이션 이름, 지속 시간 등)를 얻을 수 있습니다.

## 예제
### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onanimationiteration 예제</title>
    <style>
        .animate {
            animation: spin 2s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <div class="animate" id="myElement">회전하는 요소</div>

    <script>
        const element = document.getElementById('myElement');
        element.onanimationiteration = function(event) {
            console.log('애니메이션이 반복되었습니다: ' + event.animationName);
        };
    </script>
</body>
</html>
```

## 설명
### 일반적인 문제 및 주의사항
- **이벤트가 발생하지 않음**: CSS 애니메이션이 제대로 설정되어 있지 않거나, 애니메이션이 한 번도 시작되지 않은 경우 이벤트가 발생하지 않을 수 있습니다. 애니메이션이 정상적으로 작동하는지 확인하세요.
- **중복 이벤트 감지**: 애니메이션이 여러 번 반복될 경우, 이벤트 핸들러가 여러 번 호출될 수 있습니다. 이를 방지하려면 플래그를 사용하거나, 특정 조건을 추가하여 이벤트 호출을 제어할 수 있습니다.
- **브라우저 호환성**: 대부분의 최신 브라우저에서 지원하지만, 구형 브라우저에서는 동작이 다를 수 있으니 확인이 필요합니다.

## 한 줄 요약
`onanimationiteration`은 CSS 애니메이션이 반복될 때 발생하는 이벤트로, JavaScript를 통해 애니메이션 반복 시 특정 작업을 처리할 수 있게 해줍니다.