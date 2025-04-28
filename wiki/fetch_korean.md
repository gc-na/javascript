<!--
Meta Description: # JavaScript에서 Fetch API: 비동기 HTTP 요청 처리하기 ## 개요 JavaScript의 Fetch API는 네트워크 요청을 비동기적으로 처리할 수 있는 현대적인 방법을 제공하며, 주로 서버에서 데이터를 가져오거나 서버에 데이터를 전송하는 데 사용됩...
Meta Keywords: fetch, response, error, json, 요청을
-->

# JavaScript에서 Fetch API: 비동기 HTTP 요청 처리하기

## 개요
JavaScript의 Fetch API는 네트워크 요청을 비동기적으로 처리할 수 있는 현대적인 방법을 제공하며, 주로 서버에서 데이터를 가져오거나 서버에 데이터를 전송하는 데 사용됩니다.

## 문서화
Fetch API는 `fetch()` 함수를 통해 HTTP 요청을 보낼 수 있도록 설계되었습니다. 이 함수는 Promise를 반환하므로, 비동기 작업을 간편하게 처리할 수 있습니다. 기본적인 사용법은 다음과 같습니다:

### 목적
- 서버와 클라이언트 간의 데이터 통신을 쉽게 처리할 수 있도록 돕습니다.
- 비동기적으로 데이터를 가져오고 처리할 수 있게 해줍니다.

### 사용법
```javascript
fetch(url, options)
```
- `url`: 요청할 자원의 URL을 나타내는 문자열입니다.
- `options`: 선택적 매개변수로, 요청의 메소드, 헤더, 본문 등을 정의합니다.

### 세부사항
- 기본적으로 GET 요청을 수행하며, 다른 HTTP 메소드를 사용하는 경우 `options` 객체에서 `method` 속성을 지정해야 합니다.
- CORS 정책에 따라 다른 도메인에 대한 요청은 제한될 수 있습니다.
- JSON 데이터를 다룰 때는 `response.json()` 메소드를 사용하여 응답을 JSON 형태로 변환할 수 있습니다.

## 예제
### 기본 GET 요청
```javascript
fetch('https://api.example.com/data')
    .then(response => {
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        return response.json();
    })
    .then(data => console.log(data))
    .catch(error => console.error('There was a problem with your fetch operation:', error));
```

### POST 요청
```javascript
fetch('https://api.example.com/data', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({ key: 'value' })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

## 설명
- **CORS 문제**: 다른 도메인으로 요청을 보낼 때 CORS 정책에 의해 요청이 차단될 수 있습니다. 이 경우 서버에서 적절한 CORS 헤더를 설정해야 합니다.
- **에러 처리**: `fetch()`는 네트워크 오류가 발생한 경우에만 reject되며, HTTP 오류 상태(예: 404, 500)는 여전히 resolve됩니다. 이를 처리하기 위해 `response.ok` 속성을 확인해야 합니다.
- **AbortController**: 요청을 취소할 수 있는 `AbortController`와 함께 사용할 수 있습니다.

## 한줄 요약
Fetch API는 JavaScript에서 비동기 HTTP 요청을 간편하게 처리할 수 있는 방법입니다.