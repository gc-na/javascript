<!--
Meta Description: # WebSocketStream: 자바스크립트에서의 실시간 데이터 통신 ## 개요 WebSocketStream은 클라이언트와 서버 간에 실시간으로 양방향 통신을 가능하게 하는 API입니다. 이를 통해 웹 애플리케이션은 데이터의 전송 및 수신을 효율적으로 처리할 수 있습...
Meta Keywords: socket, event, function, console, websocketstream
-->

# WebSocketStream: 자바스크립트에서의 실시간 데이터 통신

## 개요
WebSocketStream은 클라이언트와 서버 간에 실시간으로 양방향 통신을 가능하게 하는 API입니다. 이를 통해 웹 애플리케이션은 데이터의 전송 및 수신을 효율적으로 처리할 수 있습니다.

## 문서화

### 목적
WebSocketStream은 웹 애플리케이션에서 실시간으로 데이터를 송수신할 수 있는 API로, HTTP 요청과는 달리 연결이 지속적으로 유지됩니다. 이를 통해 낮은 지연 시간과 높은 효율성을 제공합니다.

### 사용법
WebSocketStream은 기본적으로 다음과 같은 형식으로 사용됩니다:

```javascript
const socket = new WebSocketStream('ws://example.com/socket');

// 이벤트 리스너 추가
socket.onopen = function(event) {
    console.log('Connection opened:', event);
};

socket.onmessage = function(event) {
    console.log('Message received:', event.data);
};

socket.onclose = function(event) {
    console.log('Connection closed:', event);
};

// 메시지 전송
socket.send('Hello, Server!');
```

### 상세 정보
- **WebSocketStream 생성**: `new WebSocketStream(url)`를 사용하여 WebSocketStream 객체를 생성합니다.
- **이벤트 리스너**: `onopen`, `onmessage`, `onclose` 등의 이벤트를 통해 연결 상태를 관리합니다.
- **메시지 전송**: `send(data)` 메서드를 사용하여 서버에 메시지를 보낼 수 있습니다.
- **연결 종료**: `close()` 메서드를 호출하여 연결을 종료할 수 있습니다.

## 예제

### 기본 사용 예제
```javascript
const socket = new WebSocketStream('ws://example.com/socket');

socket.onopen = function() {
    console.log('연결이 열렸습니다.');
    socket.send('안녕하세요, 서버!');
};

socket.onmessage = function(event) {
    console.log('서버로부터 메시지 수신:', event.data);
};

socket.onclose = function() {
    console.log('연결이 닫혔습니다.');
};
```

### 에러 처리 예제
```javascript
socket.onerror = function(event) {
    console.error('WebSocket 오류 발생:', event);
};
```

## 설명
WebSocketStream을 사용할 때 주의해야 할 점은 다음과 같습니다:
- **연결 상태**: 연결이 맺어진 후에만 메시지를 전송해야 하며, 연결 상태를 체크하는 것이 중요합니다.
- **서버 지원**: 모든 서버가 WebSocket 프로토콜을 지원하지 않으므로, 서버 측에서 WebSocket을 지원하는지 확인해야 합니다.
- **보안**: WebSocket은 보안상의 이유로 `wss://` 프로토콜을 사용하는 것이 좋습니다.

## 한 줄 요약
WebSocketStream은 자바스크립트를 통해 클라이언트와 서버 간의 실시간 양방향 데이터 통신을 가능하게 하는 API입니다.