<!--
Meta Description: # TouchList: 자바스크립트에서의 터치 이벤트 리스트 ## 개요 TouchList는 JavaScript에서 터치 이벤트와 관련된 객체로, 사용자의 터치 입력을 관리하고 이벤트 처리에 필요한 정보를 제공합니다. 모바일 기기에서의 사용자 인터랙션을 처리하는데 필수적...
Meta Keywords: targettouches, 이벤트, touches, event, touchlist는
-->

# TouchList: 자바스크립트에서의 터치 이벤트 리스트

## 개요
TouchList는 JavaScript에서 터치 이벤트와 관련된 객체로, 사용자의 터치 입력을 관리하고 이벤트 처리에 필요한 정보를 제공합니다. 모바일 기기에서의 사용자 인터랙션을 처리하는데 필수적인 요소입니다.

## 문서화
TouchList는 `TouchEvent` 객체의 속성으로 포함되어 있으며, 사용자가 화면을 터치할 때 발생하는 모든 터치 정보를 담고 있습니다. TouchList는 여러 개의 터치를 동시에 처리할 수 있는 기능을 제공하여, 멀티 터치 제스처를 구현하는 데 유용합니다.

### 목적
TouchList의 주요 목적은 여러 터치 포인트를 추적하고 이들에 대한 정보를 제공하여 웹 애플리케이션에서 터치 기반의 인터랙션을 지원하는 것입니다.

### 사용법
TouchList는 `touches`, `targetTouches`, `changedTouches` 속성을 통해 접근할 수 있습니다. 각 속성은 다음과 같은 기능을 합니다:

- **touches**: 현재 화면에 터치되고 있는 모든 터치 포인트의 리스트입니다.
- **targetTouches**: 현재 이벤트의 대상 요소에 터치된 터치 포인트의 리스트입니다.
- **changedTouches**: 이벤트 발생 시 변경된 터치 포인트의 리스트입니다.

```javascript
element.addEventListener('touchstart', function(event) {
    const touchList = event.touches;
    console.log(touchList.length); // 현재 화면에 있는 터치의 수
});
```

## 예제
아래는 터치 이벤트에서 TouchList를 사용하는 간단한 예제입니다.

### 예제 1: 터치 시작 이벤트
```javascript
document.addEventListener('touchstart', function(event) {
    const touches = event.touches; // 현재 화면에 있는 모든 터치
    console.log(`터치 수: ${touches.length}`);
});
```

### 예제 2: 멀티 터치 이벤트
```javascript
document.addEventListener('touchmove', function(event) {
    const targetTouches = event.targetTouches; // 대상 요소에 있는 터치
    for(let i = 0; i < targetTouches.length; i++) {
        console.log(`터치 ${i + 1}: X=${targetTouches[i].clientX}, Y=${targetTouches[i].clientY}`);
    }
});
```

## 설명
TouchList를 사용할 때 주의해야 할 점은 다음과 같습니다:

1. **터치 이벤트의 순서**: 터치 이벤트는 `touchstart`, `touchmove`, `touchend`의 순서로 발생하므로 각 이벤트의 사용 시점에 따라 TouchList의 내용이 다를 수 있습니다.
2. **브라우저 호환성**: 일부 오래된 브라우저에서는 TouchList가 지원되지 않을 수 있으므로, 사용하기 전에 호환성을 확인해야 합니다.
3. **성능 문제**: 많은 터치 포인트를 동시에 처리할 경우, 성능 저하가 발생할 수 있으므로 필요하지 않은 경우에는 이벤트 리스너를 적절히 제거해야 합니다.

## 한 줄 요약
TouchList는 JavaScript에서 터치 이벤트를 관리하고 여러 터치 포인트를 추적하는 객체입니다.