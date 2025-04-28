<!--
Meta Description: # JavaScript의 "onunhandledrejection" 이벤트: Promise 거부 처리 ## 개요 `onunhandledrejection` 이벤트는 JavaScript의 Promise에서 발생하는 거부(unhandled rejection)를 처리하기 위해 ...
Meta Keywords: onunhandledrejection, 이벤트는, promise, event, promise가
-->

# JavaScript의 "onunhandledrejection" 이벤트: Promise 거부 처리

## 개요
`onunhandledrejection` 이벤트는 JavaScript의 Promise에서 발생하는 거부(unhandled rejection)를 처리하기 위해 사용됩니다. 이 이벤트는 Promise가 거부되었지만 이를 처리하기 위한 `catch` 핸들러가 없는 경우에 발생하며, 전역적으로 비동기 오류를 관리하는 데 유용합니다.

## 문서화

### 목적
`onunhandledrejection` 이벤트는 Promise가 거부되었을 때 발생하며, 이 이벤트를 통해 개발자는 에러를 추적하고 사용자에게 적절한 피드백을 제공할 수 있습니다. 이는 비동기 프로그래밍에서의 안정성을 높이는 데 기여합니다.

### 사용법
`onunhandledrejection` 이벤트는 전역 `window` 객체에 등록할 수 있습니다. 이벤트 리스너를 추가하여 Promise의 거부를 감지하고, 적절한 에러 처리를 수행할 수 있습니다.

```javascript
window.onunhandledrejection = function(event) {
    console.log('Unhandled rejection: ', event.reason);
};
```

### 세부사항
- `event.reason`: 거부된 Promise의 이유를 나타냅니다. 이 속성을 사용하여 발생한 에러에 대한 정보에 접근할 수 있습니다.
- 이 이벤트는 비동기 코드의 오류를 중앙집중식으로 관리할 수 있게 해주며, 개발자가 놓칠 수 있는 오류를 포착하는 데 도움을 줍니다.
- `unhandledrejection` 이벤트는 Promise가 거부된 후에 `catch` 핸들러가 호출되지 않았을 때 발생합니다.

## 예제

### 기본 사용 예
```javascript
// Promise가 거부될 수 있는 예
let promise = new Promise((resolve, reject) => {
    reject(new Error("Something went wrong!"));
});

// unhandledrejection 이벤트 핸들러 등록
window.onunhandledrejection = function(event) {
    console.log('Unhandled rejection: ', event.reason);
};

// Promise를 거부시키지만, catch 핸들러를 등록하지 않음
promise;
```

### 다른 예제
```javascript
// 비동기 함수에서 Promise를 사용하는 예
async function fetchData() {
    throw new Error("Failed to fetch data");
}

// unhandledrejection 이벤트 핸들러 등록
window.onunhandledrejection = function(event) {
    console.error('Unhandled rejection: ', event.reason);
};

// 비동기 호출
fetchData();
```

## 설명
- **일반적인 함정**: `onunhandledrejection` 이벤트는 모든 Promise 거부에 대해 발생하지 않습니다. Promise가 거부된 후 적절한 `catch` 블록이 있는 경우에는 이 이벤트가 발생하지 않습니다.
- **브라우저 호환성**: 대부분의 최신 브라우저에서 지원되지만, 구형 브라우저에서는 지원되지 않을 수 있습니다. 이러한 경우에는 다른 방법으로 에러를 처리해야 합니다.
- **디버깅 도구 활용**: 브라우저의 디버깅 도구를 사용하여 Promise 거부와 관련된 이벤트를 모니터링하면 더 나은 오류 추적이 가능해집니다.

## 한 줄 요약
`onunhandledrejection` 이벤트는 JavaScript에서 처리되지 않은 Promise 거부를 감지하고 처리하기 위해 사용됩니다.