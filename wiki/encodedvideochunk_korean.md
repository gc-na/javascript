<!--
Meta Description: # EncodedVideoChunk: 자바스크립트 비디오 인코딩을 위한 객체 ## 개요 `EncodedVideoChunk`는 자바스크립트에서 비디오 인코딩 작업을 수행할 때 사용하는 객체로, 비디오 데이터를 효율적으로 처리하고 전송하기 위해 설계되었습니다. 이 객체는 ...
Meta Keywords: 비디오, encodedvideochunk, 있습니다, 데이터를, 데이터
-->

# EncodedVideoChunk: 자바스크립트 비디오 인코딩을 위한 객체

## 개요
`EncodedVideoChunk`는 자바스크립트에서 비디오 인코딩 작업을 수행할 때 사용하는 객체로, 비디오 데이터를 효율적으로 처리하고 전송하기 위해 설계되었습니다. 이 객체는 비디오 스트림의 인코딩된 데이터 조각을 나타내며, WebCodecs API의 일부로 기능합니다.

## 문서화

### 목적
`EncodedVideoChunk`는 비디오 스트림의 인코딩된 데이터 블록을 표현하는 데 사용됩니다. 비디오 처리 애플리케이션에서 이 객체를 사용하여 인코딩된 비디오 데이터를 관리하고 전달할 수 있습니다.

### 사용법
`EncodedVideoChunk` 객체는 다음과 같은 속성을 가집니다:

- `type`: 비디오 데이터의 유형을 나타내는 문자열. 일반적으로 'key' 또는 'delta' 값을 가집니다.
- `timestamp`: 비디오 데이터가 생성된 시각을 나노초 단위로 나타내는 숫자.
- `data`: 인코딩된 비디오 데이터를 포함하는 `ArrayBuffer` 객체.

`EncodedVideoChunk` 객체는 기본적으로 WebCodecs API와 함께 사용됩니다. 이 API를 통해 비디오 데이터를 인코딩하고 디코딩할 수 있습니다.

### 예제
아래는 `EncodedVideoChunk` 객체를 생성하고 사용하는 간단한 예제입니다.

```javascript
// EncodedVideoChunk 객체 생성
const videoChunk = new EncodedVideoChunk({
    type: 'key', // 또는 'delta'
    timestamp: 123456789, // 타임스탬프 (나노초)
    data: new Uint8Array([/* 비디오 데이터 */]),
});

// 비디오 청크 사용 예
console.log(videoChunk.type); // 'key'
console.log(videoChunk.timestamp); // 123456789
console.log(videoChunk.data); // Uint8Array(비디오 데이터)
```

## 설명
`EncodedVideoChunk` 객체를 사용할 때 몇 가지 주의해야 할 사항이 있습니다:

- **타입 확인**: `type` 속성의 값이 'key' 또는 'delta'인지 확인해야 합니다. 잘못된 값은 비디오 처리에서 오류를 발생시킬 수 있습니다.
- **타임스탬프의 정밀도**: 타임스탬프는 나노초 단위로 제공되므로, 필요에 따라 적절한 단위로 변환하여 사용할 수 있습니다.
- **데이터 포맷**: `data` 속성에 제공되는 `ArrayBuffer`는 올바른 비디오 인코딩 포맷이어야 합니다. 그렇지 않으면 비디오 플레이어에서 재생되지 않을 수 있습니다.

## 한 줄 요약
`EncodedVideoChunk`는 자바스크립트에서 비디오 인코딩 데이터를 효율적으로 처리하기 위한 객체로, WebCodecs API의 일환으로 활용됩니다.