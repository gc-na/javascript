<!--
Meta Description: # onwebkitAnimationIteration: 자바스크립트에서의 애니메이션 반복 이벤트 ## 개요 `onwebkitAnimationIteration`은 웹 애니메이션에서 반복되는 각 이터레이션이 완료될 때 발생하는 이벤트입니다. 이 이벤트는 CSS 애니메이션이 ...
Meta Keywords: onwebkitanimationiteration, 애니메이션이, 때마다, 애니메이션, css
-->

# onwebkitAnimationIteration: 자바스크립트에서의 애니메이션 반복 이벤트

## 개요
`onwebkitAnimationIteration`은 웹 애니메이션에서 반복되는 각 이터레이션이 완료될 때 발생하는 이벤트입니다. 이 이벤트는 CSS 애니메이션이 반복될 때마다 특정 작업을 수행할 수 있도록 도와줍니다.

## 문서화

### 목적
`onwebkitAnimationIteration`은 CSS 애니메이션이 반복될 때마다 호출되는 이벤트 핸들러를 설정하기 위해 사용됩니다. 이 이벤트를 사용하면 애니메이션의 각 반복 단계에서 추가적인 동작을 정의할 수 있습니다.

### 사용법
`onwebkitAnimationIteration` 이벤트는 JavaScript의 이벤트 리스너로 설정할 수 있으며, CSS 애니메이션이 완료될 때마다 호출됩니다. 사용 방법은 다음과 같습니다:

```javascript
element.onwebkitAnimationIteration = function(event) {
    // 애니메이션 반복 시 실행할 코드
};
```

여기서 `element`는 애니메이션이 적용된 HTML 요소입니다. 이 요소에 `onwebkitAnimationIteration` 이벤트 리스너를 추가하여 애니메이션 반복 시 원하는 동작을 정의할 수 있습니다.

### 세부사항
- `onwebkitAnimationIteration`는 웹킷 기반 브라우저에서 CSS 애니메이션이 반복될 때마다 발생합니다.
- 이 이벤트는 `AnimationEvent` 객체를 반환하며, 애니메이션의 이름, 지속 시간, 타이밍 함수 등을 포함한 정보에 접근할 수 있습니다.

## 예제

### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Animation Example</title>
    <style>
        @keyframes myAnimation {
            from { transform: translateX(0); }
            to { transform: translateX(100px); }
        }
        .animated {
            animation: myAnimation 1s infinite;
        }
    </style>
</head>
<body>
    <div class="animated" id="myElement">애니메이션 요소</div>
    <script>
        const element = document.getElementById('myElement');
        element.onwebkitAnimationIteration = function(event) {
            console.log('애니메이션 반복됨: ' + event.animationName);
        };
    </script>
</body>
</html>
```
위 예제에서는 `myElement`라는 요소에 애니메이션이 적용되며, 애니메이션이 반복될 때마다 메시지가 콘솔에 출력됩니다.

## 설명
`onwebkitAnimationIteration`을 사용할 때 주의할 점:
- 모든 브라우저에서 지원되지 않을 수 있으므로, 크로스 브라우징을 고려해야 합니다. 최신 브라우저에서는 `animationiteration` 이벤트를 사용하는 것이 좋습니다.
- 애니메이션이 너무 자주 반복되면 성능 문제가 발생할 수 있으므로, 애니메이션의 반복 횟수를 적절히 조정해야 합니다.

## 한 줄 요약
`onwebkitAnimationIteration`은 CSS 애니메이션이 반복될 때마다 발생하는 이벤트로, 애니메이션의 각 반복 단계에서 특정 작업을 수행할 수 있게 해줍니다.