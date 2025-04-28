<!--
Meta Description: # SourceBufferList: 자바스크립트의 소스 버퍼 리스트 ## 개요 `SourceBufferList`는 HTML5의 Media Source Extensions (MSE)의 일부로, 비디오 및 오디오 스트림의 동적 처리를 가능하게 하는 객체입니다. 이 객체는 ...
Meta Keywords: sourcebuffer, mediasource, sourcebufferlist, 미디어, 있습니다
-->

# SourceBufferList: 자바스크립트의 소스 버퍼 리스트

## 개요
`SourceBufferList`는 HTML5의 Media Source Extensions (MSE)의 일부로, 비디오 및 오디오 스트림의 동적 처리를 가능하게 하는 객체입니다. 이 객체는 여러 개의 `SourceBuffer`를 포함하고 있으며, 이들을 관리하고 조작하는 데 사용됩니다.

## 문서화
### 목적
`SourceBufferList`는 `MediaSource` 객체와 함께 사용되어, 미디어 스트림에 데이터를 추가하거나 수정할 수 있도록 돕습니다. 여러 `SourceBuffer`를 통해 다양한 미디어 소스를 동시에 처리할 수 있는 기능을 제공합니다.

### 사용법
`SourceBufferList`는 `MediaSource` 객체에서 `sourceBuffers` 속성을 통해 접근할 수 있습니다. 이 속성은 `SourceBuffer` 객체의 배열을 반환하며, 각 `SourceBuffer`는 미디어 데이터를 포함하고 있습니다.

```javascript
// MediaSource 객체 생성
const mediaSource = new MediaSource();
const sourceBufferList = mediaSource.sourceBuffers;

// sourceBufferList를 사용하여 각 SourceBuffer에 접근
sourceBufferList.forEach((sourceBuffer) => {
    console.log(sourceBuffer);
});
```

### 세부사항
- `SourceBufferList`는 `length` 속성을 가지며, 이를 통해 현재 포함된 `SourceBuffer`의 수를 확인할 수 있습니다.
- `SourceBuffer` 객체는 다양한 메서드를 제공하여, 데이터 추가, 삭제, 및 업데이트가 가능합니다. 

## 예제
```javascript
// MediaSource 객체 생성
const mediaSource = new MediaSource();

// 비디오 요소에 MediaSource 적용
const videoElement = document.querySelector('video');
videoElement.src = URL.createObjectURL(mediaSource);

// 미디어 소스가 준비되었을 때
mediaSource.addEventListener('sourceopen', () => {
    // SourceBuffer 추가
    const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8"');
    
    // 데이터 추가
    fetch('video.webm')
        .then(response => response.arrayBuffer())
        .then(data => {
            sourceBuffer.appendBuffer(data);
        });
});
```

## 설명
`SourceBufferList`를 사용할 때 몇 가지 주의할 점이 있습니다:
- `SourceBuffer`는 여러 개의 미디어 형식을 지원하지만, 모든 형식이 모든 브라우저에서 지원되는 것은 아닙니다. 따라서 사용하기 전에 호환성을 확인해야 합니다.
- `SourceBuffer`에 대한 데이터 추가는 비동기적으로 이루어지므로, 데이터가 추가되기 전에 여러 동작을 시도할 경우 오류가 발생할 수 있습니다.
- `SourceBuffer`가 비어있거나, 이미 추가한 데이터가 있을 경우, `appendBuffer` 메서드의 호출 시 주의해야 합니다.

## 한 줄 요약
`SourceBufferList`는 HTML5 MSE의 일환으로, 여러 `SourceBuffer`를 관리하여 동적인 미디어 스트림 처리를 가능하게 하는 자바스크립트 객체입니다.