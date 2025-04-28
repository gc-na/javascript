<!--
Meta Description: # ontransitionrun: 자바스크립트에서의 사용법과 특징 ## 개요 `ontransitionrun`은 CSS 전환이 시작되었을 때 발생하는 이벤트로, JavaScript를 통해 HTML 요소의 스타일 변화에 대한 반응을 추가할 수 있게 해줍니다. 이 이벤트를 ...
Meta Keywords: element, 전환이, ontransitionrun, 있습니다, html
-->

# ontransitionrun: 자바스크립트에서의 사용법과 특징

## 개요
`ontransitionrun`은 CSS 전환이 시작되었을 때 발생하는 이벤트로, JavaScript를 통해 HTML 요소의 스타일 변화에 대한 반응을 추가할 수 있게 해줍니다. 이 이벤트를 활용하면 사용자 인터페이스(UI)의 동적 효과를 향상시킬 수 있습니다.

## 문서화

### 목적
`ontransitionrun` 이벤트는 CSS 전환이 실행될 때마다 호출되며, 이를 통해 개발자는 전환이 시작될 때 특정 작업을 수행할 수 있습니다. 예를 들어, 애니메이션 효과를 추가하거나 사용자에게 알림을 표시하는 등의 기능을 구현할 수 있습니다.

### 사용법
`ontransitionrun` 이벤트는 JavaScript에서 이벤트 리스너를 통해 사용할 수 있습니다. 아래는 기본적인 사용법입니다.

```javascript
const element = document.querySelector('.my-element');

element.addEventListener('transitionrun', (event) => {
    console.log('Transition is running on:', event.target);
});
```

이 코드는 `.my-element` 클래스를 가진 요소에서 전환이 시작될 때마다 콘솔에 메시지를 출력합니다.

### 세부 사항
- 이 이벤트는 CSS 전환이 활성화된 모든 요소에 대해 발생합니다.
- IE11과 같은 일부 구형 브라우저는 이 이벤트를 지원하지 않으므로, 브라우저 호환성에 유의해야 합니다.
- 이 이벤트는 `transitionend` 이벤트와 함께 사용되는 경우가 많습니다. 후자는 전환이 완료되었을 때 발생합니다.

## 예제

### 기본 사용 예제
아래는 `ontransitionrun` 이벤트를 활용한 간단한 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Transition Run Example</title>
    <style>
        .my-element {
            width: 100px;
            height: 100px;
            background-color: blue;
            transition: background-color 2s;
        }
        .my-element.active {
            background-color: red;
        }
    </style>
</head>
<body>
    <div class="my-element"></div>
    <button id="toggle">Toggle Color</button>

    <script>
        const element = document.querySelector('.my-element');
        const button = document.getElementById('toggle');

        element.addEventListener('transitionrun', () => {
            console.log('Transition is running!');
        });

        button.addEventListener('click', () => {
            element.classList.toggle('active');
        });
    </script>
</body>
</html>
```

이 예제에서는 버튼을 클릭할 때마다 요소의 배경색이 파란색에서 빨간색으로 전환되며, 전환이 시작될 때마다 콘솔에 메시지가 출력됩니다.

## 설명
- **일관성 없는 브라우저 지원**: `ontransitionrun`은 최신 브라우저에선 잘 지원되지만, 구형 브라우저에서는 제대로 동작하지 않을 수 있으므로, 브라우저 호환성을 항상 확인해야 합니다.
- **전환 속도**: 전환의 지속시간은 CSS의 `transition` 속성에 의해 정의됩니다. 이 속성이 설정되지 않으면 `ontransitionrun` 이벤트가 발생하지 않을 수 있습니다.
- **이벤트 흐름**: 이 이벤트는 전환이 시작될 때 발생하며, 이후 `transitionend` 이벤트가 발생합니다. 이를 통해 전환의 시작과 끝을 모두 관리할 수 있습니다.

## 요약
`ontransitionrun`은 CSS 전환이 시작될 때 발생하는 이벤트로, JavaScript를 통해 UI의 동적인 반응을 추가할 수 있게 해줍니다.