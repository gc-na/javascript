<!--
Meta Description: # JavaScript Response 객체: 웹 응답 처리의 모든 것 ## 개요 JavaScript의 Response 객체는 Fetch API를 사용하여 HTTP 요청에 대한 응답을 처리하는 데 사용됩니다. 이 객체는 서버로부터 받은 응답의 상태, 헤더, 본문 등을 ...
Meta Keywords: response, fetch, error, 객체는, then
-->

# JavaScript Response 객체: 웹 응답 처리의 모든 것

## 개요
JavaScript의 Response 객체는 Fetch API를 사용하여 HTTP 요청에 대한 응답을 처리하는 데 사용됩니다. 이 객체는 서버로부터 받은 응답의 상태, 헤더, 본문 등을 포함하며, 웹 애플리케이션에서 비동기적으로 데이터를 가져올 때 필수적입니다.

## 문서화

### 목적
Response 객체는 Fetch API의 결과로 생성되며, 클라이언트가 서버로부터 받은 응답을 다루기 위해 사용됩니다. 이를 통해 HTTP 응답의 정보를 쉽게 접근하고 처리할 수 있습니다.

### 사용법
Response 객체는 Fetch API의 `fetch()` 메서드로부터 반환됩니다. 기본적인 사용법은 다음과 같습니다:

```javascript
fetch('https://api.example.com/data')
  .then(response => {
    // Response 객체를 사용하여 응답 처리
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

### 세부사항
Response 객체는 다음과 같은 주요 속성과 메서드를 포함합니다:

- **status**: HTTP 응답 상태 코드 (예: 200, 404 등).
- **statusText**: 상태 코드와 관련된 텍스트 메시지.
- **headers**: 응답 헤더를 포함하는 Headers 객체.
- **url**: 응답을 받은 URL.
- **ok**: 응답 상태 코드가 200-299 범위에 있을 경우 true.
- **body**: 응답 본문을 읽기 위한 ReadableStream.
- **json()**: 응답 본문을 JSON으로 변환하는 메서드.
- **text()**: 응답 본문을 텍스트로 변환하는 메서드.
- **blob()**: 응답 본문을 Blob 객체로 변환하는 메서드.

## 예제
### 기본 사용 예
```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('Fetch error:', error);
  });
```

### Blob 사용 예
```javascript
fetch('https://example.com/image.png')
  .then(response => response.blob())
  .then(imageBlob => {
    const imageUrl = URL.createObjectURL(imageBlob);
    const img = document.createElement('img');
    img.src = imageUrl;
    document.body.appendChild(img);
  });
```

## 설명
Response 객체를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **상태 코드 확인**: 응답이 성공적이지 않을 경우(예: 404, 500 등) `response.ok`를 확인하여 적절한 오류 처리를 해야 합니다.
- **비동기 처리**: Fetch API는 비동기적으로 작동하므로, `then()` 체인을 통해 응답을 처리해야 합니다.
- **본문 형식**: 응답 본문은 JSON, 텍스트, Blob 등 다양한 형식으로 변환할 수 있으므로, 필요한 형식에 맞는 메서드를 선택해야 합니다.

## 한 줄 요약
JavaScript의 Response 객체는 Fetch API를 통해 서버의 HTTP 응답을 처리하는 데 필요한 정보를 제공합니다.