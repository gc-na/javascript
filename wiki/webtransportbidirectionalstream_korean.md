<!--
Meta Description: # WebTransportBidirectionalStream: JavaScript에서의 양방향 스트리밍 ## 개요 `WebTransportBidirectionalStream`은 웹 애플리케이션에서 저지연 양방향 데이터 전송을 가능하게 하는 API로, 실시간 통신을 지원...
Meta Keywords: 데이터, transport, webtransportbidirectionalstream, const, await
-->

# WebTransportBidirectionalStream: JavaScript에서의 양방향 스트리밍

## 개요
`WebTransportBidirectionalStream`은 웹 애플리케이션에서 저지연 양방향 데이터 전송을 가능하게 하는 API로, 실시간 통신을 지원합니다. 이 API는 WebTransport 프로토콜을 기반으로 하여 클라이언트와 서버 간의 데이터 전송을 효율적으로 처리할 수 있습니다.

## 문서화
### 목적
`WebTransportBidirectionalStream`은 클라이언트와 서버 간의 양방향 데이터 스트림을 생성하여 데이터 패킷의 빠르고 안정적인 전송을 가능하게 합니다. 주로 실시간 애플리케이션, 온라인 게임, 비디오 스트리밍, 화상 회의 등에서 사용됩니다.

### 사용법
`WebTransportBidirectionalStream`은 `WebTransport` 객체의 `bidirectionalStream()` 메소드를 통해 생성됩니다. 다음은 그 기본적인 사용법입니다.

```javascript
const transport = new WebTransport('wss://example.com/transport');
await transport.ready;

const stream = await transport.bidirectionalStream();
```

### 세부사항
- 스트림은 데이터의 송신과 수신을 동시에 처리할 수 있으며, `ReadableStream`과 `WritableStream`을 사용하여 쉽게 데이터 흐름을 관리할 수 있습니다.
- 스트림은 HTTP/3 프로토콜을 기반으로 하여 더 빠르고 안정적인 데이터 전송을 보장합니다.
- `WebTransportBidirectionalStream`은 Promise를 반환하며, 스트림이 준비되면 이를 사용하여 데이터를 송신하거나 수신할 수 있습니다.

## 예제
### 기본 사용 예제
아래 예제는 클라이언트가 서버에 메시지를 송신하고, 서버로부터 응답을 받는 과정을 보여줍니다.

```javascript
const transport = new WebTransport('wss://example.com/transport');

async function startStream() {
    await transport.ready;
    const stream = await transport.bidirectionalStream();

    const writer = stream.writable.getWriter();
    const reader = stream.readable.getReader();

    // 메시지 송신
    await writer.write(new TextEncoder().encode('Hello, Server!'));

    // 응답 수신
    const { done, value } = await reader.read();
    if (!done) {
        console.log('서버 응답:', new TextDecoder().decode(value));
    }

    writer.releaseLock();
    reader.releaseLock();
}

startStream().catch(console.error);
```

## 설명
### 일반적인 문제 및 주의사항
- `WebTransportBidirectionalStream`은 브라우저에서 지원해야 사용할 수 있습니다. 따라서 브라우저의 호환성을 확인해야 합니다.
- 연결이 끊어지거나 오류가 발생할 경우 적절한 예외 처리를 구현해야 합니다.
- 데이터 패킷의 순서가 보장되지 않으므로, 필요한 경우 애플리케이션 레벨에서 패킷 순서를 관리해야 합니다.

## 한 줄 요약
`WebTransportBidirectionalStream`은 웹 애플리케이션에서 실시간 양방향 데이터 전송을 가능하게 하는 API입니다.