<!--
Meta Description: # WebSocket: JavaScript를 이용한 실시간 통신 기술 ## 개요 WebSocket은 클라이언트와 서버 간의 지속적이고 양방향 통신을 가능하게 하는 프로토콜로, JavaScript를 통해 쉽게 구현할 수 있습니다. 이 기술은 주로 실시간 데이터 전송이 필...
Meta Keywords: socket, websocket, 연결이, function, console
-->

# WebSocket: JavaScript를 이용한 실시간 통신 기술

## 개요
WebSocket은 클라이언트와 서버 간의 지속적이고 양방향 통신을 가능하게 하는 프로토콜로, JavaScript를 통해 쉽게 구현할 수 있습니다. 이 기술은 주로 실시간 데이터 전송이 필요한 애플리케이션, 예를 들어 채팅 애플리케이션, 실시간 게임, 주식 거래 플랫폼 등에서 사용됩니다.

## 문서화

### 목적
WebSocket은 HTTP 프로토콜과 달리, 클라이언트와 서버 간의 연결을 지속적으로 유지하여 데이터 전송을 실시간으로 가능하게 합니다. 이는 서버가 클라이언트에게 데이터를 푸시할 수 있다는 장점이 있습니다.

### 사용법
JavaScript에서 WebSocket을 사용하기 위해서는 `WebSocket` 객체를 생성하고 서버에 연결한 후, 메시지를 송수신하는 방식으로 진행됩니다.

```javascript
// WebSocket 객체 생성
const socket = new WebSocket('ws://example.com/socket');

// 연결이 열렸을 때 호출되는 이벤트 핸들러
socket.onopen = function(event) {
    console.log('WebSocket 연결이 열렸습니다.');
    socket.send('Hello Server!');
};

// 서버로부터 메시지를 수신했을 때 호출되는 이벤트 핸들러
socket.onmessage = function(event) {
    console.log('서버로부터 메시지 수신:', event.data);
};

// 오류가 발생했을 때 호출되는 이벤트 핸들러
socket.onerror = function(error) {
    console.error('WebSocket 오류 발생:', error);
};

// 연결이 닫혔을 때 호출되는 이벤트 핸들러
socket.onclose = function(event) {
    console.log('WebSocket 연결이 닫혔습니다.');
};
```

## 예제
### 기본 사용 예제
아래의 코드는 WebSocket을 사용하여 서버와 연결하고 메시지를 송수신하는 간단한 예제입니다.

```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.onopen = function() {
    console.log('연결이 성공적으로 열렸습니다.');
    socket.send('안녕하세요, 서버!');
};

socket.onmessage = function(event) {
    console.log('받은 메시지:', event.data);
};

socket.onclose = function() {
    console.log('연결이 닫혔습니다.');
};
```

## 설명
### 일반적인 실수 및 주의 사항
1. **CORS 정책**: WebSocket도 Cross-Origin Resource Sharing(CORS) 정책을 따릅니다. 서버에서 Cross-Origin 요청을 허용하도록 설정해야 합니다.
2. **연결 상태**: `WebSocket`의 상태를 항상 체크해야 합니다. 예를 들어, `socket.readyState`를 통해 연결 상태를 확인하고, 연결이 열려 있을 때만 메시지를 전송해야 합니다.
3. **에러 처리**: 서버와의 연결이 끊어지거나 에러가 발생할 경우를 대비해 적절한 에러 핸들링 코드를 작성해야 합니다.

## 한 줄 요약
WebSocket은 JavaScript를 이용해 클라이언트와 서버 간의 지속적이고 양방향 실시간 통신을 가능하게 하는 프로토콜입니다.