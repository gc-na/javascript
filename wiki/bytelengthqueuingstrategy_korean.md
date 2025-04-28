<!--
Meta Description: # ByteLengthQueuingStrategy: 자바스크립트에서의 바이트 길이 대기 전략 ## 개요 `ByteLengthQueuingStrategy`는 스트림에서 데이터를 처리할 때 큐의 길이를 바이트 단위로 측정하여 제어하는 데 사용되는 전략입니다. 이 전략은 특...
Meta Keywords: bytelengthqueuingstrategy, 바이트, 데이터, new, highwatermark
-->

# ByteLengthQueuingStrategy: 자바스크립트에서의 바이트 길이 대기 전략

## 개요
`ByteLengthQueuingStrategy`는 스트림에서 데이터를 처리할 때 큐의 길이를 바이트 단위로 측정하여 제어하는 데 사용되는 전략입니다. 이 전략은 특히 바이너리 데이터 전송 시 유용하며, 웹 스트림 API와 함께 사용됩니다.

## 문서화
`ByteLengthQueuingStrategy`는 스트림 API의 일부로, 데이터의 크기(바이트)를 기준으로 큐의 상태를 결정합니다. 주로 `ReadableStream` 또는 `WritableStream`의 생성 시에 사용됩니다. 이 전략을 통해 데이터의 크기에 따라 스트림이 얼마나 많은 데이터를 버퍼링할지를 제어할 수 있습니다.

### 목적
이 전략의 주된 목적은 데이터 전송의 효율을 높이고, 메모리 사용량을 관리하는 것입니다. 예를 들어, 큰 바이너리 파일을 처리할 때, 각 데이터 조각의 바이트 길이에 따라 흐름을 조절할 수 있습니다.

### 사용법
`ByteLengthQueuingStrategy`를 사용하려면, 다음과 같이 생성할 수 있습니다:

```javascript
const strategy = new ByteLengthQueuingStrategy({
  highWaterMark: 1024 // 큐의 최대 바이트 수
});
```

`highWaterMark`는 큐에 저장될 수 있는 최대 바이트 수를 설정합니다. 이 값을 초과하면 스트림이 일시 중지됩니다.

## 예제
아래는 `ByteLengthQueuingStrategy`를 사용한 기본 예제입니다:

```javascript
const { ReadableStream, WritableStream } = require('stream/web');

const readable = new ReadableStream({
  start(controller) {
    // 데이터 추가
    controller.enqueue(new Uint8Array([1, 2, 3]));
    controller.enqueue(new Uint8Array([4, 5, 6]));
    controller.close();
  }
}, new ByteLengthQueuingStrategy({ highWaterMark: 6 }));

const writable = new WritableStream({
  write(chunk) {
    console.log(`Received chunk of length: ${chunk.byteLength}`);
  }
}, new ByteLengthQueuingStrategy({ highWaterMark: 6 }));

readable.pipeTo(writable);
```

이 예제에서는 `ReadableStream`을 생성하고, `WritableStream`으로 데이터를 전송합니다. 큐의 최대 바이트 수를 6으로 설정하여 데이터 흐름을 제어합니다.

## 설명
`ByteLengthQueuingStrategy`를 사용할 때 주의해야 할 점은 `highWaterMark` 값입니다. 이 값이 너무 낮으면 데이터 처리 속도가 느려질 수 있고, 너무 높으면 메모리 사용량이 증가할 수 있습니다. 또한, 스트림의 사용 목적에 따라 적절한 값으로 설정해야 합니다.

일부 브라우저에서는 스트림 API 지원이 제한적일 수 있으므로, 사용하기 전에 호환성을 확인하는 것이 좋습니다.

## 한 줄 요약
`ByteLengthQueuingStrategy`는 자바스크립트에서 스트림의 데이터 큐를 바이트 단위로 제어하여 효율적인 데이터 전송을 가능하게 하는 전략입니다.