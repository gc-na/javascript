<!--
Meta Description: # JavaScript SharedWorker: 멀티쓰레드 웹 애플리케이션을 위한 공유 워커 ## 개요 SharedWorker는 웹 애플리케이션에서 여러 브라우저 탭이 동일한 워커 스레드를 공유할 수 있게 해주는 JavaScript 기능입니다. 이를 통해 데이터의 일관...
Meta Keywords: worker, port, sharedworker, function, shared
-->

# JavaScript SharedWorker: 멀티쓰레드 웹 애플리케이션을 위한 공유 워커

## 개요
SharedWorker는 웹 애플리케이션에서 여러 브라우저 탭이 동일한 워커 스레드를 공유할 수 있게 해주는 JavaScript 기능입니다. 이를 통해 데이터의 일관성을 유지하고, 성능을 향상시키며, 리소스를 절약할 수 있습니다.

## 문서화

### 목적
SharedWorker는 여러 제어 컨텍스트(예: 여러 탭, 프레임)가 상호 작용할 수 있는 공통의 스레드를 생성함으로써, 웹 애플리케이션의 멀티쓰레드 작업을 가능하게 합니다. 이를 통해 데이터 전송 및 처리를 효율적으로 관리할 수 있습니다.

### 사용법
SharedWorker를 사용하려면, 먼저 `SharedWorker` 생성자를 사용하여 워커를 생성합니다. 그 후, `port`를 통해 메시지를 주고받을 수 있습니다.

```javascript
// shared-worker.js
self.onconnect = function(event) {
    const port = event.ports[0];
    port.onmessage = function(e) {
        port.postMessage('Hello from SharedWorker: ' + e.data);
    };
};
```

```javascript
// main.js
const worker = new SharedWorker('shared-worker.js');

worker.port.onmessage = function(e) {
    console.log(e.data); // 'Hello from SharedWorker: ...'
};

worker.port.postMessage('Hello Worker');
```

## 예제
1. **기본 SharedWorker 사용 예제**

```javascript
// shared-worker.js
self.onconnect = function(event) {
    const port = event.ports[0];
    port.onmessage = function(e) {
        port.postMessage('Received: ' + e.data);
    };
};

// main.js
const worker = new SharedWorker('shared-worker.js');

worker.port.onmessage = function(e) {
    console.log(e.data);
};

worker.port.postMessage('Test message from main.js');
```

2. **여러 탭에서의 SharedWorker 사용 예제**

```javascript
// shared-worker.js
self.onconnect = function(event) {
    const port = event.ports[0];
    port.onmessage = function(e) {
        port.postMessage('Broadcast: ' + e.data);
    };
};

// tab1.js
const worker = new SharedWorker('shared-worker.js');
worker.port.onmessage = function(e) {
    console.log('Tab1 received: ', e.data);
};
worker.port.postMessage('Message from Tab 1');

// tab2.js
const worker = new SharedWorker('shared-worker.js');
worker.port.onmessage = function(e) {
    console.log('Tab2 received: ', e.data);
};
worker.port.postMessage('Message from Tab 2');
```

## 설명
### 일반적인 문제점 및 추가 사항
- **지원 브라우저:** SharedWorker는 모든 브라우저에서 지원되지 않습니다. 특히 Internet Explorer에서는 지원하지 않으므로, 호환성 문제를 고려해야 합니다.
- **메시지 포트:** 각 탭이나 프레임은 `port`를 통해 SharedWorker와 통신합니다. 포트는 독립적이므로, 각 포트에서 받는 메시지는 서로 영향을 미치지 않습니다.
- **자원 관리:** SharedWorker는 생성된 이후에도 여러 탭에서 공유되므로, 자원 관리가 중요합니다. 불필요한 메시지 전송을 피하고, 사용이 끝난 후에는 포트를 닫아야 합니다.

## 한 줄 요약
SharedWorker는 JavaScript를 사용하여 여러 브라우저 탭 간에 공통의 워커 스레드를 공유함으로써 데이터 전송을 효율적으로 관리할 수 있는 기능입니다.