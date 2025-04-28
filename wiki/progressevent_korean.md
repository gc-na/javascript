<!--
Meta Description: # ProgressEvent: JavaScript에서 진행 상태 이벤트 처리 ## 개요 `ProgressEvent`는 JavaScript에서 비동기 작업의 진행 상태를 추적하고 처리하는 데 사용되는 이벤트입니다. 주로 네트워크 요청과 파일 업로드와 같은 작업에서 사용되...
Meta Keywords: event, const, xhr, progressevent, loaded
-->

# ProgressEvent: JavaScript에서 진행 상태 이벤트 처리

## 개요
`ProgressEvent`는 JavaScript에서 비동기 작업의 진행 상태를 추적하고 처리하는 데 사용되는 이벤트입니다. 주로 네트워크 요청과 파일 업로드와 같은 작업에서 사용되며, 프로세스의 진행률을 사용자에게 알릴 수 있도록 돕습니다.

## 문서화
`ProgressEvent`는 DOM 이벤트의 일종으로, 특정 작업의 진행 상황에 대한 정보를 제공합니다. 이 이벤트는 일반적으로 `XMLHttpRequest` 객체와 `Fetch API`와 같은 네트워크 요청에서 발생합니다. `ProgressEvent`는 다음과 같은 속성을 포함합니다:

- `lengthComputable`: 진행 상황을 계산할 수 있는지 여부를 나타내는 Boolean 값입니다.
- `loaded`: 현재까지 로드된 바이트 수를 나타냅니다.
- `total`: 전체 파일 크기 또는 요청의 전체 크기를 나타내는 바이트 수입니다.

### 사용법
`ProgressEvent`는 이벤트 리스너를 통해 처리할 수 있습니다. 예를 들어, `XMLHttpRequest` 객체의 `onprogress` 이벤트 핸들러를 사용하여 진행률을 추적할 수 있습니다.

```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'your-url-here', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Progress: ${percentComplete}%`);
    } else {
        console.log(`Loaded: ${event.loaded} bytes`);
    }
};

xhr.onload = function() {
    console.log('Request completed successfully');
};

xhr.send();
```

## 예제
### 1. 기본 `ProgressEvent` 사용
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://example.com/file', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Downloaded ${percentComplete}%`);
    } else {
        console.log(`Loaded ${event.loaded} bytes`);
    }
};

xhr.send();
```

### 2. Fetch API와 함께 사용
```javascript
async function fetchData(url) {
    const response = await fetch(url);
    const reader = response.body.getReader();
    let receivedLength = 0;
    const contentLength = +response.headers.get('Content-Length');

    while (true) {
        const { done, value } = await reader.read();
        if (done) break;

        receivedLength += value.length;
        const percentComplete = (receivedLength / contentLength) * 100;
        console.log(`Downloaded ${percentComplete}%`);
    }
}

fetchData('https://example.com/large-file');
```

## 설명
`ProgressEvent`를 사용할 때 주의해야 할 점은 `lengthComputable` 속성이 항상 `true`가 아닐 수 있다는 것입니다. 이 경우, 전체 진행 상황을 알 수 없으므로, 단순히 `loaded`만 로그에 출력해야 합니다. 또한, 모든 요청에서 이 이벤트가 발생하는 것은 아니므로, 특정 상황에서만 이벤트가 발생할 수 있다는 점을 유의해야 합니다.

## 한 줄 요약
`ProgressEvent`는 JavaScript에서 비동기 작업의 진행 상황을 추적할 수 있게 해주는 이벤트입니다.