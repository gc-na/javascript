<!--
Meta Description: # JavaScript onanimationend 이벤트: 애니메이션 종료 감지하기 ## 개요 `onanimationend` 이벤트는 CSS 애니메이션이 종료될 때 발생하는 이벤트입니다. 이 이벤트를 통해 JavaScript에서 애니메이션의 완료 시점을 감지하고, 그에...
Meta Keywords: 애니메이션이, onanimationend, 애니메이션, 이벤트, css
-->

# JavaScript onanimationend 이벤트: 애니메이션 종료 감지하기

## 개요
`onanimationend` 이벤트는 CSS 애니메이션이 종료될 때 발생하는 이벤트입니다. 이 이벤트를 통해 JavaScript에서 애니메이션의 완료 시점을 감지하고, 그에 따라 추가적인 동작을 실행할 수 있습니다.

## 문서
`onanimationend`는 DOM 이벤트 중 하나로, CSS 애니메이션이 끝날 때 자동으로 호출됩니다. 이 이벤트는 주로 애니메이션 효과가 완료된 후 특정 작업을 수행하기 위해 사용됩니다. 예를 들어, 특정 요소의 스타일을 변경하거나, 애니메이션이 끝난 후 다른 애니메이션을 시작하는 데 유용합니다.

### 사용법
`onanimationend` 이벤트는 다음과 같이 사용할 수 있습니다:

```javascript
element.onanimationend = function(event) {
    // 애니메이션 종료 후 실행할 코드
};
```

또는 `addEventListener` 메서드를 사용하여 보다 유연하게 이벤트를 처리할 수 있습니다:

```javascript
element.addEventListener('animationend', function(event) {
    // 애니메이션 종료 후 실행할 코드
});
```

### 이벤트 속성
이벤트 객체는 다음과 같은 유용한 속성을 포함합니다:
- `animationName`: 종료된 애니메이션의 이름
- `elapsedTime`: 애니메이션이 완료되는 데 걸린 시간
- `pseudoElement`: 애니메이션이 적용된 가상 요소 (예: `::before`, `::after`)

## 예제
아래는 `onanimationend` 이벤트를 사용하는 기본적인 예제입니다:

```html
<div id="box" class="animate"></div>

<style>
    .animate {
        width: 100px;
        height: 100px;
        background-color: red;
        animation: example 2s forwards;
    }

    @keyframes example {
        from { background-color: red; }
        to { background-color: blue; }
    }
</style>

<script>
    const box = document.getElementById('box');
    
    box.addEventListener('animationend', function(event) {
        console.log(`애니메이션 "${event.animationName}"이 종료되었습니다.`);
        box.style.opacity = 0; // 애니메이션 종료 후 요소 숨기기
    });
</script>
```

## 설명
`onanimationend` 이벤트를 사용할 때 주의해야 할 점은, 여러 애니메이션이 동시에 실행되는 경우입니다. 이럴 경우, 이벤트 리스너가 여러 번 호출될 수 있으며, 각 애니메이션에 따라 적절한 처리를 해야 합니다. 이를 위해 이벤트 객체의 `animationName` 속성을 활용하여 어떤 애니메이션이 끝났는지를 확인하고 조건부 로직을 구현하는 것이 좋습니다.

또한, CSS 애니메이션이 제대로 작동하지 않거나, 이벤트가 발생하지 않는 경우, CSS 속성이나 애니메이션이 올바르게 설정되었는지 확인해야 합니다.

## 한 줄 요약
`onanimationend`는 CSS 애니메이션이 종료될 때 발생하는 이벤트로, JavaScript에서 애니메이션 완료 시점을 감지하여 추가 작업을 수행하는 데 유용합니다.