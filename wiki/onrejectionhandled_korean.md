<!--
Meta Description: # JavaScript의 onrejectionhandled: Promise 거부 처리에 대한 완벽 가이드 ## 개요 `onrejectionhandled`는 JavaScript의 Promise API에서 제공하는 이벤트로, Promise가 거부(rejected)된 후 이...
Meta Keywords: onrejectionhandled, promise, promise가, 거부가, 이벤트는
-->

# JavaScript의 onrejectionhandled: Promise 거부 처리에 대한 완벽 가이드

## 개요
`onrejectionhandled`는 JavaScript의 Promise API에서 제공하는 이벤트로, Promise가 거부(rejected)된 후 이를 처리하는 핸들러를 설정할 수 있게 해줍니다. 이 이벤트는 Promise의 거부가 처리될 때 발생하며, 개발자가 오류 처리 로직을 정의할 수 있는 기회를 제공합니다.

## 문서화
`onrejectionhandled` 이벤트는 Promise가 거부된 후, 해당 거부를 처리하는 방법에 대한 제어를 제공하여 비동기 코드의 안정성을 높입니다. 이 이벤트는 전역 객체인 `window`에서 발생하며, Promise의 거부가 처리될 때마다 호출됩니다.

### 목적
- 비동기 작업에서 발생하는 오류를 중앙집중식으로 관리할 수 있게 해줍니다.
- Promise의 거부가 정상적으로 처리될 때 이벤트를 감지할 수 있습니다.

### 사용법
`onrejectionhandled` 이벤트는 전역 객체에 설정하여 사용할 수 있습니다. 이 이벤트는 구문적으로 다음과 같이 정의됩니다:

```javascript
window.onrejectionhandled = function(event) {
    // 거부 처리 로직
    console.log('거부가 처리되었습니다:', event.promise);
};
```

이벤트 핸들러는 `event` 객체를 인수로 받아, 어떤 Promise가 거부되었는지, 그리고 그 거부가 어떻게 처리되었는지를 알 수 있습니다.

## 예제
### 기본 사용 예
아래 코드는 Promise가 거부된 후, 이를 `onrejectionhandled` 이벤트로 처리하는 예시입니다.

```javascript
// 전역 onrejectionhandled 설정
window.onrejectionhandled = function(event) {
    console.log('거부된 Promise가 처리되었습니다:', event.promise);
};

// Promise 생성 및 거부
const myPromise = new Promise((resolve, reject) => {
    reject(new Error('예외 발생'));
});

// 거부 처리
myPromise.catch(error => {
    console.error('Promise가 거부되었습니다:', error);
});
```

위의 코드에서 Promise가 거부되면, `onrejectionhandled` 이벤트가 호출되고, 거부된 Promise에 대한 정보가 로그로 출력됩니다.

## 설명
### 일반적인 함정 및 주의사항
1. **비동기 오류 처리**: `onrejectionhandled`는 Promise가 거부된 후, 해당 거부가 처리될 때 발생합니다. 따라서 비동기 작업에서 발생하는 오류를 놓칠 수 있습니다.
2. **전역 핸들러 설정**: 이벤트 핸들러를 설정할 때, 다른 전역 핸들러와 충돌하지 않도록 주의해야 합니다. 기존의 핸들러를 덮어쓰지 않도록 `addEventListener` 메서드를 사용하는 것이 좋습니다.
3. **Promise 체이닝**: Promise 체이닝을 사용할 때, 중간에 발생한 거부가 최종적으로 처리되지 않으면 `unhandledrejection` 이벤트가 발생할 수 있습니다. 이를 방지하기 위해 항상 `catch` 메서드를 사용하여 모든 거부를 처리해야 합니다.

## 한 줄 요약
`onrejectionhandled`는 JavaScript에서 Promise 거부가 처리될 때 발생하는 이벤트로, 비동기 오류 처리를 중앙집중식으로 관리할 수 있게 해줍니다.