<!--
Meta Description: # PageTransitionEvent: 자바스크립트에서 페이지 전환 이벤트 이해하기 ## 개요 `PageTransitionEvent`는 웹 페이지 간의 전환이 발생할 때 발생하는 이벤트로, 페이지 전환 애니메이션이나 효과를 구현하는 데 유용합니다. 이 이벤트는 사용자...
Meta Keywords: 페이지, pagetransitionevent, event, 페이지가, window
-->

# PageTransitionEvent: 자바스크립트에서 페이지 전환 이벤트 이해하기

## 개요
`PageTransitionEvent`는 웹 페이지 간의 전환이 발생할 때 발생하는 이벤트로, 페이지 전환 애니메이션이나 효과를 구현하는 데 유용합니다. 이 이벤트는 사용자가 페이지를 이동할 때 발생하며, 페이지 전환의 상태를 추적하고 제어할 수 있는 방법을 제공합니다.

## 문서화

### 목적
`PageTransitionEvent`는 사용자가 페이지를 이동할 때 발생하는 다양한 사건을 감지하고 처리할 수 있도록 해주는 이벤트입니다. 이 이벤트는 주로 SPA(Single Page Application)와 같은 동적인 웹 애플리케이션에서 페이지 전환 효과를 구현하는 데 사용됩니다.

### 사용법
`PageTransitionEvent`는 `popstate` 이벤트와 함께 사용되며, 주로 `window` 객체에서 발생합니다. 이 이벤트는 다음과 같은 속성을 가집니다:

- `target`: 이벤트가 발생한 대상
- `currentTarget`: 이벤트 리스너가 연결된 대상
- `timeStamp`: 이벤트가 발생한 시간

```javascript
window.addEventListener('pagehide', function (event) {
    console.log('페이지가 숨겨졌습니다.');
});

window.addEventListener('pageshow', function (event) {
    console.log('페이지가 표시되었습니다.');
});
```

## 예시

### 기본 사용 예시

```javascript
window.addEventListener('pageshow', function(event) {
    if (event.persisted) {
        console.log("페이지 캐시에서 복원되었습니다.");
    } else {
        console.log("새 페이지가 로드되었습니다.");
    }
});
```

### 페이지 숨기기 예시

```javascript
window.addEventListener('pagehide', function(event) {
    console.log("페이지가 숨겨지고 있습니다.");
});
```

## 설명
`PageTransitionEvent`와 관련된 일반적인 문제점은 다음과 같습니다:

- **이벤트 중복**: 페이지 전환 시 여러 번 이벤트가 발생할 수 있으므로, 이벤트 핸들러가 중복 실행되지 않도록 주의해야 합니다.
- **캐시 문제**: 페이지가 캐시에서 복원될 때와 새로운 페이지가 로드될 때의 동작이 다를 수 있으므로, `event.persisted` 속성을 사용하여 이를 처리해야 합니다.
- **호환성**: 모든 브라우저에서 동일하게 지원되지 않으므로, 브라우저 호환성을 고려해야 합니다.

## 한 줄 요약
`PageTransitionEvent`는 페이지 전환 시 발생하는 이벤트로, 웹 애플리케이션에서 페이지 전환 애니메이션과 효과를 구현하는 데 유용합니다.