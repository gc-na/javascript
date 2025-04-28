<!--
Meta Description: # PromiseRejectionEvent: 자바스크립트에서의 비동기 오류 처리 ## 개요 `PromiseRejectionEvent`는 JavaScript에서 비동기 작업이 실패했을 때 발생하는 이벤트입니다. 이 이벤트는 Promise가 거부(rejected)될 때 발...
Meta Keywords: promise가, promiserejectionevent, 있습니다, 이벤트, 비동기
-->

# PromiseRejectionEvent: 자바스크립트에서의 비동기 오류 처리

## 개요
`PromiseRejectionEvent`는 JavaScript에서 비동기 작업이 실패했을 때 발생하는 이벤트입니다. 이 이벤트는 Promise가 거부(rejected)될 때 발생하며, 이를 통해 개발자는 Promise의 거부 원인을 추적하고 오류를 처리할 수 있습니다.

## 문서화

### 목적
`PromiseRejectionEvent`는 비동기 프로그래밍에서 발생할 수 있는 오류를 보다 효과적으로 관리하기 위해 설계되었습니다. 이 이벤트는 Promise가 거부되었을 때 발생하며, 개발자는 해당 이벤트를 수신하여 적절한 오류 처리 로직을 구현할 수 있습니다.

### 사용법
`PromiseRejectionEvent`는 `unhandledrejection` 이벤트 리스너를 통해 처리됩니다. 이 이벤트 리스너는 Promise가 거부되었지만 처리되지 않은 경우에 호출됩니다. 다음은 이를 설정하는 기본적인 방법입니다.

```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.log('Unhandled promise rejection:', event.reason);
});
```

이벤트 리스너 내에서 `event.reason`을 사용하여 거부된 Promise의 이유를 확인할 수 있습니다.

### 세부 사항
- **이벤트 타입**: `PromiseRejectionEvent`
- **프로퍼티**:
  - `reason`: Promise가 거부된 이유를 나타내는 값입니다. 예를 들어, 오류 객체 또는 문자열이 될 수 있습니다.
- **일반적인 사용 예**: 애플리케이션에서 비동기 작업을 사용할 때 오류를 추적하고 사용자에게 적절한 피드백을 제공하는 데 유용합니다.

## 예제

### 기본 사용 예
아래는 Promise가 거부될 때 `unhandledrejection` 이벤트가 발생하는 예제입니다.

```javascript
function faultyPromise() {
    return new Promise((resolve, reject) => {
        reject(new Error("Something went wrong!"));
    });
}

faultyPromise();

window.addEventListener('unhandledrejection', function(event) {
    console.log('Unhandled promise rejection:', event.reason);
});
```

위 코드에서 `faultyPromise` 함수는 거부된 Promise를 반환하며, `unhandledrejection` 이벤트 리스너가 이를 감지하여 오류 메시지를 콘솔에 출력합니다.

## 설명
`PromiseRejectionEvent`와 관련된 일반적인 문제는 Promise가 거부되었지만 처리되지 않은 경우 발생합니다. 이 경우, 개발자는 예상치 못한 오류가 발생할 수 있으며, 애플리케이션의 안정성이 저하될 수 있습니다. 따라서, 항상 Promise가 거부될 경우 이를 적절히 처리하는 것이 중요합니다. 또한, 이벤트 리스너를 여러 번 등록할 수 있으므로 중복 등록을 피하는 것이 좋습니다.

## 한 줄 요약
`PromiseRejectionEvent`는 JavaScript에서 비동기 Promise가 거부되었을 때 발생하는 이벤트로, 이를 통해 개발자는 오류를 효과적으로 관리할 수 있습니다.