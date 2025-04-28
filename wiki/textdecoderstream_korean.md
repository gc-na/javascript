<!--
Meta Description: # TextDecoderStream: JavaScript의 텍스트 디코딩을 위한 스트림 API ## 개요 `TextDecoderStream`은 JavaScript에서 텍스트 데이터의 디코딩을 위한 스트림 처리 API입니다. 이 기능은 인코딩된 바이트 스트림을 읽어서 유...
Meta Keywords: textdecoderstream, 있습니다, utf, 바이트, new
-->

# TextDecoderStream: JavaScript의 텍스트 디코딩을 위한 스트림 API

## 개요
`TextDecoderStream`은 JavaScript에서 텍스트 데이터의 디코딩을 위한 스트림 처리 API입니다. 이 기능은 인코딩된 바이트 스트림을 읽어서 유니코드 문자열로 변환하는 데 사용됩니다. 웹 애플리케이션에서 네트워크 통신이나 파일 읽기 시 유용하게 활용될 수 있습니다.

## 문서화

### 목적
`TextDecoderStream`은 다양한 문자 인코딩을 지원하며, 스트림 형태로 데이터를 처리할 수 있도록 해줍니다. 이는 대량의 데이터를 메모리에 한 번에 로드하지 않고도 처리할 수 있는 효율적인 방법입니다.

### 사용법
`TextDecoderStream`을 사용하기 위해서는 먼저 인스턴스를 생성해야 합니다. 생성 시 원하는 문자 인코딩을 지정할 수 있습니다. 주로 사용되는 인코딩으로는 UTF-8, UTF-16, ISO-8859-1 등이 있습니다.

```javascript
const decoderStream = new TextDecoderStream('utf-8');
```

이 스트림은 `ReadableStream`과 `WritableStream`의 조합으로 작동하며, 보통 `ReadableStream`과 함께 사용됩니다. 데이터를 디코딩하기 위해서는 `pipeTo()` 메소드를 사용하여 데이터 흐름을 연결합니다.

### 세부 사항
- **인코딩**: 생성 시 지정한 인코딩 방식에 따라 데이터가 디코딩됩니다.
- **스트림 사용**: `TextDecoderStream`은 비동기 처리를 지원하여, 대량의 데이터를 효율적으로 처리할 수 있습니다.
- **에러 처리**: 잘못된 인코딩으로 인한 에러가 발생할 수 있으며, 이러한 경우에는 `TextDecoder`의 `fatal` 옵션을 통해 에러 발생 시 스트림이 중단되도록 설정할 수 있습니다.

## 예제

### 기본 사용 예제
```javascript
const { ReadableStream } = require('stream/web');
const decoderStream = new TextDecoderStream('utf-8');

// 바이트 배열을 스트림으로 변환
const byteStream = new ReadableStream({
    start(controller) {
        // 예시로 UTF-8 인코딩된 바이트 추가
        controller.enqueue(new Uint8Array([72, 101, 108, 108, 111])); // 'Hello'의 UTF-8 바이트
        controller.close();
    }
});

// 바이트 스트림을 디코더 스트림에 연결
byteStream.pipeThrough(decoderStream).getReader().read().then(({ value }) => {
    console.log(value); // 'Hello' 출력
});
```

### 에러 처리 예제
```javascript
const decoderStream = new TextDecoderStream('utf-8', { fatal: true });

const byteStream = new ReadableStream({
    start(controller) {
        controller.enqueue(new Uint8Array([255])); // 잘못된 UTF-8 바이트
        controller.close();
    }
});

byteStream.pipeThrough(decoderStream).getReader().read().catch((error) => {
    console.error('Decoding error:', error); // 에러 처리
});
```

## 설명
- **일관된 데이터 처리**: `TextDecoderStream`을 사용하면, 데이터의 흐름을 일관되게 처리할 수 있습니다. 특히 대규모 데이터의 경우, 메모리 효율적인 방식으로 처리할 수 있습니다.
- **비동기적 특성**: 스트림은 비동기적으로 작동하므로, UI가 블로킹되지 않으면서도 데이터 처리를 수행할 수 있습니다.
- **인코딩 미지원 문제**: 사용자가 지정한 인코딩이 지원되지 않거나 잘못된 경우, 에러가 발생할 수 있으므로 항상 에러 처리를 구현하는 것이 중요합니다.

## 한 줄 요약
`TextDecoderStream`은 JavaScript에서 바이트 스트림을 유니코드 문자열로 효율적으로 디코딩하는 API입니다.