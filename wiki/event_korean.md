<!--
Meta Description: # JavaScript 이벤트: 웹 개발의 핵심 요소 ## 개요 JavaScript에서 "이벤트"는 사용자 상호작용이나 다른 프로그램적 변경에 의해 발생하는 상황을 의미합니다. 이벤트는 웹 애플리케이션의 동작을 제어하고, 사용자 경험을 향상시키는 데 중요한 역할을 합니...
Meta Keywords: 이벤트, event, javascript, 리스너를, addeventlistener
-->

# JavaScript 이벤트: 웹 개발의 핵심 요소

## 개요
JavaScript에서 "이벤트"는 사용자 상호작용이나 다른 프로그램적 변경에 의해 발생하는 상황을 의미합니다. 이벤트는 웹 애플리케이션의 동작을 제어하고, 사용자 경험을 향상시키는 데 중요한 역할을 합니다.

## 문서
이벤트는 브라우저가 사용자와 상호작용할 때 발생하는 다양한 행동을 설명합니다. 일반적인 이벤트에는 클릭, 키 입력, 마우스 이동 등이 있습니다. JavaScript에서는 이러한 이벤트를 감지하고 처리하기 위해 이벤트 리스너를 사용합니다.

### 목적
이벤트를 통해 사용자는 웹 페이지와 상호작용할 수 있으며, 개발자는 이러한 상호작용에 대한 응답을 정의할 수 있습니다.

### 사용법
이벤트를 사용하기 위해서는 다음과 같은 단계를 따릅니다:

1. **이벤트 선택**: 어떤 이벤트를 감지할 것인지 선택합니다.
2. **이벤트 리스너 추가**: `addEventListener()` 메서드를 사용하여 이벤트 리스너를 추가합니다.
3. **이벤트 처리기 정의**: 이벤트가 발생했을 때 실행될 코드를 정의합니다.

```javascript
// 버튼 클릭 이벤트 예제
const button = document.getElementById('myButton');

button.addEventListener('click', function() {
    alert('버튼이 클릭되었습니다!');
});
```

## 예제
### 클릭 이벤트
```javascript
const button = document.getElementById('submitBtn');

button.addEventListener('click', function() {
    console.log('폼이 제출되었습니다.');
});
```

### 키 입력 이벤트
```javascript
document.addEventListener('keypress', function(event) {
    console.log(`키가 눌렸습니다: ${event.key}`);
});
```

### 마우스 이동 이벤트
```javascript
document.addEventListener('mousemove', function(event) {
    console.log(`마우스 위치: X=${event.clientX}, Y=${event.clientY}`);
});
```

## 설명
이벤트 처리 시 주의할 점은 다음과 같습니다:

- **이벤트 중복**: 동일한 이벤트에 여러 리스너를 추가할 수 있지만, 불필요한 중복을 피해야 합니다.
- **이벤트 전파**: 이벤트는 DOM 트리에서 전파될 수 있으며, 특정 이벤트에 대해 전파를 중지하려면 `event.stopPropagation()` 메서드를 사용할 수 있습니다.
- **성능 문제**: 너무 많은 이벤트 리스너를 추가하면 성능에 영향을 줄 수 있으므로, 필요할 때만 리스너를 추가하는 것이 좋습니다.

## 한 줄 요약
JavaScript에서 이벤트는 사용자 상호작용을 처리하고 웹 애플리케이션의 동작을 제어하는 중요한 기능입니다.