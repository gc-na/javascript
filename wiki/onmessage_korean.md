<!--
Meta Description: # JavaScript의 onmessage: 웹 워커 및 메시지 전송의 모든 것 ## 개요 `onmessage`는 JavaScript에서 웹 워커 및 메시지 통신을 처리하는 이벤트 리스너입니다. 이 기능은 다양한 스레드 간에 데이터를 안전하게 전송하고 처리할 수 있게 ...
Meta Keywords: onmessage, worker, event, 메시지, 있습니다
-->

# JavaScript의 onmessage: 웹 워커 및 메시지 전송의 모든 것

## 개요
`onmessage`는 JavaScript에서 웹 워커 및 메시지 통신을 처리하는 이벤트 리스너입니다. 이 기능은 다양한 스레드 간에 데이터를 안전하게 전송하고 처리할 수 있게 해줍니다.

## 문서화

### 목적
`onmessage`는 웹 워커나 `Window` 객체 간의 메시지를 수신하는 데 사용됩니다. 이 이벤트는 데이터가 전송될 때마다 발생하며, 이를 통해 비동기적으로 작업을 수행할 수 있습니다.

### 사용법
`onmessage`는 웹 워커의 인스턴스나 `window` 객체에서 이벤트 리스너로 설정할 수 있습니다. 메시지가 전달되면, 해당 메시지를 처리하기 위한 콜백 함수가 호출됩니다.

```javascript
// 웹 워커에서의 사용 예
self.onmessage = function(event) {
    console.log('메시지 수신:', event.data);
    // 메시지에 대한 처리 로직
};

// 메인 스크립트에서의 사용 예
const worker = new Worker('worker.js');

worker.onmessage = function(event) {
    console.log('작업 완료:', event.data);
};

// 메시지 전송
worker.postMessage('작업 시작');
```

## 예시
### 기본 사용 예
```javascript
// 메인 스크립트
const worker = new Worker('worker.js');

worker.onmessage = function(event) {
    console.log('수신한 메시지:', event.data);
};

worker.postMessage('안녕하세요, 워커!');

// 워커 스크립트 (worker.js)
onmessage = function(event) {
    console.log('메인 스크립트로부터:', event.data);
    postMessage('워커가 메시지를 수신했습니다!');
};
```

## 설명
`onmessage`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **데이터 형식**: `postMessage`로 전송하는 데이터는 객체, 문자열, 배열 등 다양한 형식이 가능하지만, 순환 참조가 있는 객체는 전송할 수 없습니다.
  
2. **보안**: 웹 워커는 동일 출처 정책을 따르므로, 다른 도메인 간의 메시지 전송은 제한됩니다.

3. **비동기 처리**: `onmessage` 이벤트는 비동기적으로 처리되므로, 이벤트가 발생하는 시점에 따라 코드의 실행 순서가 달라질 수 있습니다. 이 점을 고려하여 코드를 작성해야 합니다.

## 한 줄 요약
`onmessage`는 JavaScript에서 웹 워커와 메시지 통신을 처리하는 이벤트 리스너로, 비동기 데이터 전송을 가능하게 합니다.